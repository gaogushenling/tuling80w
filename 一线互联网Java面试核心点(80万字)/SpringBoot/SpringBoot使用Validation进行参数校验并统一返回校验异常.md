# SpringBoot 使用 Validation 进行参数校验并统一返回校验异常

在 SpringBoot项目开发中，有一个观点是不要相信前端传入的参数，因为你不知道用户是怎么操作我们接口的，所以在后端也需要对参数进行校验，这篇文章主要讲讲我们项目中最常使用的验证方案。

### 引入相应的依赖
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-validation</artifactId>
</dependency>
```
spring-boot-starter-validation本质是使用的Hibernate Validator，它并没有自己的实现。

### Validation的基本校验注解
| **注解** | **描述** |
| --- | --- |
| **@Null** | 验证对象是否为null |
| **@NotNull** | 验证对象是否不为null，无法检查长度为0的字符串 |
| **@NotBlank** | 检查约束字符串是否为null，且被Trim后的长度是否大于0，只适用于字符串，会去掉前后空格 |
| **@NotEmpty** | 检查约束元素是否为NULL或者是EMPTY |
| **@AssertTrue** | 验证Boolean对象是否为true |
| **@AssertFalse** | 验证Boolean对象是否为false |
| **@Size(min=, max=)** | 验证对象（Array、Collection、Map、String）长度是否在给定的范围之内 |
| **@Length(min=, max=)** | 验证注解的元素值长度是否在min和max区间内 |
| **@Past** | 验证Date和Calendar对象是否在当前时间之前 |
| **@Future** | 验证Date和Calendar对象是否在当前时间之后 |
| **@Pattern** | 验证String对象是否符合正则表达式的规则 |
| **@Min** | 验证Number和String对象是否大等于指定的值 |
| **@Max** | 验证Number和String对象是否小等于指定的值 |
| **@DecimalMax** | 被标注的值必须不大于约束中指定的最大值，参数为通过BigDecimal定义的最大值的字符串表示，小数存在精度 |
| **@DecimalMin** | 被标注的值必须不小于约束中指定的最小值，参数为通过BigDecimal定义的最小值的字符串表示，小数存在精度 |
| **@Digits** | 验证Number和String的构成是否合法 |
| **@Digits(integer=,fraction=)** | 验证字符串是否符合指定格式的数字，**integer**指定整数精度，**fraction**指定小数精度 |
| **@Range(min=, max=)** | 验证注解的元素值在最小值和最大值之间 |
| **@Range(min=10000,max=50000,message="range.bean.wage")** | 验证注解的元素值在最小值10000和最大值50000之间，自定义错误信息为"range.bean.wage" |
| **@Valid** | 写在方法参数前，递归地对该对象进行校验，如果关联对象是集合或数组，则对其中的元素进行递归校验；如果是一个map，则对其中的值部分进行校验（是否进行递归验证） |
| **@CreditCardNumber** | 信用卡验证 |
| **@Email** | 验证是否是邮件地址，如果为null，不进行验证，算通过验证 |
| **@ScriptAssert(lang= ,script=, alias=)** | 自定义脚本验证 |
| **@URL(protocol=,host=, port=,regexp=, flags=)** | 验证URL的格式是否正确，可以指定协议 |


### 添加参数校验
在我们对应的DTO上并在controller的上添加校验。

#### 在DTO的属性上添加校验	
通过在参数上添加各种校验注解实现校验
```java
import com.fasterxml.jackson.annotation.JsonIgnore;
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;
import org.hibernate.validator.constraints.Length;

import javax.validation.constraints.Email;
import javax.validation.constraints.Max;
import javax.validation.constraints.Min;
import javax.validation.constraints.NotBlank;
import java.util.UUID;

@Data
@AllArgsConstructor
@NoArgsConstructor
public class registryUserDto {
    @NotBlank(message = "用户名不能为空")
    private String username;
    @NotBlank(message = "密码不能为空")
    @Length(min = 6, max = 20, message = "密码长度在6-20之间")
    private String password;
    @Min(value = 0, message = "年龄最小为0")
    @Max(value = 200, message = "年龄最大为200")
    private Integer age;
    @NotBlank(message = "邮箱不能为空")
    @Email(message = "邮箱格式不正确")
    private String email;
    @JsonIgnore
    private String salt = UUID.randomUUID().toString().replaceAll("-", "");
    private Boolean admin;
}
```

#### 在controller对应的DTO添加@Valid或者@Validated
```java
@PostMapping("/registry")
public ResponseResult registryUser(@RequestBody @Valid registryUserDto registryUserDto) {
    return ResponseResult.okResult(registryUserDto);
}
```
这样添加后就可以对其中的参数实现校验了，当校验失败时接口就会返回`500`异常和相应的异常信息。

#### 对于复杂String校验我们可以使用正则来校验，如下所示：
```java
@Pattern(regexp = "^1(3|4|5|7|8)\d{9}$",message = "手机号码格式错误")
@NotBlank(message = "手机号码不能为空")
private String phone;
```
另外对于单个参数的校验，没有用DTO对象来接收的参数也可以校验，先在controller类上添加@Validated，再在对应的参数前加校验注解，如下所示：
```java
@RestController
@RequestMapping("/user")
@Validated
public class UserController {
    @PostMapping("/registry")
    public ResponseResult registryUser(@NotBlank(message = "name不能为空") String name) {
        return ResponseResult.okResult(name);
    }
}
```

### 自定义校验注解
对于一些常见的或复杂的校验需要我们需要自定义校验注解，实现如下：

#### 新建自定义注解
```java
import org.beiming.validator.StatusValidator;

import javax.validation.Constraint;
import javax.validation.Payload;
import java.lang.annotation.*;

@Target({ElementType.FIELD, ElementType.PARAMETER})
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Constraint(validatedBy = {StatusValidator.class})
public @interface Status {

    String[] statusType() default {};

    String message() default "状态传递有误";

    Class<?>[] groups() default {};

    Class<? extends Payload>[] payload() default {};

}

```

#### 实现相应的校验
```java
import org.beiming.annotation.validator.Status;

import javax.validation.ConstraintValidator;
import javax.validation.ConstraintValidatorContext;
import java.util.Arrays;
import java.util.List;

public class StatusValidator implements ConstraintValidator<Status, Integer> {

    private List<String> typeStatus ;

    @Override
    public void initialize(Status constraintAnnotation) {
        typeStatus = Arrays.asList(constraintAnnotation.statusType());
        ConstraintValidator.super.initialize(constraintAnnotation);
    }

    @Override
    public boolean isValid(Integer value, ConstraintValidatorContext constraintValidatorContext) {
        if(value !=null){
            if(!typeStatus.contains(String.valueOf(value))){
                return false;
            }
        }
        return true;
    }
}
```

#### 自定义注解的使用
```java
@Status(statusType = {"1", "2"})
private Integer status;
```

### 校验失败统一异常处理
大家可以看到我们上面校验失败的响应msg非常不友好，有很多前端不需要知道的消息。在统一异常处理中添加BindException的处理:
```java
import org.beiming.enums.AppHttpCodeEnum;
import org.beiming.exception.SystemException;
import org.beiming.domain.vo.ResponseResult;
import lombok.extern.slf4j.Slf4j;
import org.springframework.validation.BindException;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.RestControllerAdvice;

@RestControllerAdvice
@Slf4j
public class GlobalExceptionHandler {
    @ExceptionHandler(SystemException.class)
    public ResponseResult systemExceptionHandler(SystemException e) {
        log.error("出现了异常! {}", e);
        return ResponseResult.errorResult(e.getCode(), e.getMsg());
    }
    @ExceptionHandler(Exception.class)
    public ResponseResult exceptionHandler(Exception e) {
        log.error("出现了异常! {}", e);
        return ResponseResult.errorResult(AppHttpCodeEnum.SYSTEM_ERROR.getCode(), e.getMessage());
    }
    /* 添加校验参数异常处理 */
    @ExceptionHandler(BindException.class)
    public ResponseResult bindExceptionHandler(BindException e) {
        log.error("出现了异常! {}", e);
        return ResponseResult.errorResult(AppHttpCodeEnum.SYSTEM_ERROR, e.getBindingResult().getAllErrors().get(0).getDefaultMessage());
    }
}
```
可以看到异常信息非常友好，也非常方便前端弹出消息框提示！这样就在SpringBoot的项目中添加了参数校验及统一异常处理，其实整体非常简单，也希望大家在项目中用起来！



> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/wmnvt8drzfi50eae>