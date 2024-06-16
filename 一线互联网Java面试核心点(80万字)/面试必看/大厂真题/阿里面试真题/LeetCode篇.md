# LeetCode篇

【Python语法】
```
reduce(function, iterable[, initializer])    reduce(lambda x,y:x * y,ns) # 数组之乘积 (ns[0] * ns[1]) * ns[2]    reduce(lambda x,y:x + y,ns) # 数组之和# 记忆化搜索@functools.lru_cache(None)res = helper(0,N,0)helper.cache_clear()tuple(ns) 可以hash做参数# 大根堆q = list(map(lambda x:-x,ns))heapq.heapify(q)key = -heapq.heappop(q)# 过滤函数filter(function, iterable)    filter(lambda x: 2 < x < 10 and x % 2 == 0, range(18))    filter(dfs, range(len(graph)))# 除数div, mod = divmod(sum(ns), 4)random.randint(i,len(self.ns)-1)#第一个降序，第二个升序sorted(pss,key = lambda x:[x[0],-x[1]])
# 不可变str 常见函数split(sep=None, maxsplit=-1)  # 以sep来分割字符串strip([chars])  # 去除首末两端的字符, 默认是 \r,\n," "join(iterable)  # 将iterable内的元素拼接成字符串,如','.join(['leet', 'code'])="leet,code"replace(old, new[, count])  # 字符串替换, old to newcount(sub[, start[, end]])  # 统计子字符串sub的个数startswith(prefix[, start[, end]])  # 以prefix开始的字符串endswith(suffix[, start[, end]])  # 以suffix结束的字符串cs in chrs: # chrs 中包含 cs 
# deque 常见函数queue = deque([iterable[, maxlen]])queue.append(val)  # 往右边添加一个元素queue.appendleft(val)  # 往左边添加一个元素queue.clear()  # 清空队列queue.count(val)  # 返回指定元素的出现次数queue.insert(val[, start[, stop]])  # 在指定位置插入元素queue.pop()  # 获取最右边一个元素，并在队列中删除queue.popleft()  # 获取最左边一个元素，并在队列中删除queue.reverse()  # 队列反转queue.remove(val)  # 删除指定元素queue.rotate(n=1)  # 把右边元素放到左边
# list 常见函数lst.sort(*, key=None, reverse=False)lst.append(val)  # 也可以 lst = lst + [val]lst.clear()  # 清空列表lst.count(val)  # val个数lst.pop(val=lst[-1])  # (默认)从末端移除一个值lst.remove(val)  # 移除 vallst.reverse()  # 反转lst.insert(i, val)  # 在 i 处插入 val
# 字典dict 常见函数d = defaultdict(lambda : value) # 取到不存在的值时不会报错，用{}时、需要设置get的default值pop(key[, default])  # 通过键去删除键值对(若没有该键则返回default(没有设置default则报错))setdefault(key[, default])  # 设置默认值update([other])  # 批量添加get(key[, default])  # 通过键获取值(若没有该键可设置默认值, 预防报错)clear()  # 清空字典keys()  # 将字典的键组成新的可迭代对象values()  # 将字典中的值组成新的可迭代对象items()  # 将字典的键值对凑成一个个元组, 组成新的可迭代对象dict1 = dict2 #两个字典完全相等，滑窗时可用
# 集合set 常见函数s = set(lambda : value)add(elem)  # 向集合中添加数据update(*others)  # 迭代着增加clear()  # 清空集合discard(elem)  # 删除集合中指定的值(不存在则不删除)
# 堆heapq 常见函数heap = []  # 建堆heapq.heappush(heap,item)  # 往堆中插入新值heapq.heappop(heap)  # 弹出最小的值heap[0]  # 查看堆中最小的值, 不弹出heapq.heapify(x)  # 以线性时间将一个列表转为堆heapq.heappoppush(heap, item)  # 弹出最小的值.并且将新的值插入其中.heapq.merge(*iterables, key=None, reverse=False)  # 将多个堆进行合并heapq.nlargest(n, iterable, key=None)  # 从堆中找出最大的 n 个数，key的作用和sorted( )方法里面的key类似, 用列表元素的某个属性和函数作为关键字heapq.nsmallest(n, iterable, key=None)  # 从堆中找出最小的 n 个数, 与 nlargest 相反

# 二分查找函数bisect.bisect_left(ps, T, L=0, R=len(ns))  #二分左边界bisect.bisect_right(ps, T, L=0, R=len(ns)) #二分右边界 bisect.insort_left(a, x, lo=0, hi=len(a))  # 二分插入到左侧bisect.insort_right(a, x, lo=0, hi=len(a)) # 二分插入到右侧
# bit操作& 符号，x & y ，会将两个十进制数在二进制下进行与运算| 符号，x | y ，会将两个十进制数在二进制下进行或运算^ 符号，x ^ y ，会将两个十进制数在二进制下进行异或运算<< 符号，x << y 左移操作，最右边用 0 填充>> 符号，x >> y 右移操作，最左边用 0 填充~ 符号，~x ，按位取反操作，将 x 在二进制下的每一位取反
# 整数集合set位运算# 整数集合做标志时，可以做参数加速运算vstd 访问 i ：vstd | (1 << i)vstd 离开 i ：vstd & ~(1 << i)vstd 不包含 i : not vstd & (1 << i)
并集 ：A | B交集 ：A & B全集 ：(1 << n) - 1补集 ：((1 << n) - 1) ^ A子集 ：(A & B) == B判断是否是 2 的幂 ：A & (A - 1) == 0最低位的 1 变为 0 ：n &= (n - 1)        while n:            n &= n - 1            ret += 1最低位的 1：A & (-A)，最低位的 1 一般记为 lowbit(A)
# ^     ：匹配字符串开头# [\+\-]：代表一个+字符或-字符# ?     ：前面一个字符可有可无# \d    ：一个数字# +     ：前面一个字符的一个或多个# \D    ：一个非数字字符# *     ：前面一个字符的0个或多个matches = re.match('[ ]*([+-]?\d+)', s)
```
【背包模板】
**「力扣」**上的 0-1 背包问题：

- 组合问题模板

#0-1背包，不可重复for n in ns:     for i in range(T, n-1, -1):        dp[i] = max(dp[i], dp[i - n] + ws[i])#完全背包，可重复，无序，算重量for n in ns:     for i in range(n, T+1):        dp[i] = max(dp[i], dp[i - n] + ws[i]) #完全背包，可重复，有序，算次数     for i in range(1, T+1):    for n in ns:        dp[i] += dp[i-n]

- 377 组合总和 Ⅳ
- 494 目标和
- 518 零钱兑换 II
- True、False问题

```
dp[i] |= dp[i-num]
```

- 139 单词拆分
- 416 分割等和子集

```
#特殊的可以使用bit数组
```

- 最大最小问题：

dp[i] = min(dp[i], dp[i-num]+1)dp[i] = max(dp[i], dp[i-num]+1)

- 474 一和零
- 322 零钱兑换

**「力扣」**第 879 题：盈利计划（困难）；
**「力扣」**第 1449 题：数位成本和为目标值的最大数字（困难）。
【回溯模板】
```
# 回溯算法，复杂度较高2^n或者N！，因为回溯算法就是暴力穷举，可用lru剪枝@functools.lru_cache(None)def backtrack(路径, 选择列表):    if 满足结束条件:        结果.append(路径)        return    for 选择 in 选择列表:    # 核心代码段          if vst[i]:   # 辅助数组，减枝          continue        做出选择        递归执行backtrack        撤销选择
```
**「剪枝」**第 46 题 全排列 第 47 题 全排列②
# 剪枝def backtrack(temp_list, length):    if length == n:      res.append(temp_list)    for i in range(n):      if not visited[i]:          visited[i] = 1          backtrack(temp_list + [nums[i]], length + 1)          visited[i] = 0
**「索引遍历」**第 78 题 子集 | 第 47 题 子集② | 第 131 题 分割字符串

```
第 **39 **题 组合 | 第 **40** 题 组合②  | 第 **216** 题 组合③
```
# 索引遍历def helper1(idx, n, temp_list):  if temp_list not in res:    res.append(temp_list)  for i in range(idx, n):    helper1(i + 1, n, temp_list + [nums[i]])
**「 资源消耗」**第 22 题 夸号生成
# 资源消耗def backtrack(S, L, R):  if not L and not R:    ans.append(''.join(S))    return  if L :     backtrack(S + ['('], L-1, R)  if R > L : backtrack(S + [')'], L, R-1)
**「资源消耗」**第 93 题 复原IP
资源消耗def backtrack(i, tmp, flag):  if i == n and flag == 0:    res.append(tmp[:-1])  elif i<n and s[i] == '0':    backtrack(i + 1, tmp + s[i] + ".", flag - 1)  elif flag :    for j in range(i, min(n,i + 3)):      if 0 < int(s[i:j + 1]) <= 255:        backtrack(j + 1, tmp + s[i:j + 1] + ".", flag - 1)
**「资源消耗」**第 17 题 电话号码

```
# 资源消耗def dfs(path, remains):  if not remains:    res.append(path[:])    return  for i in range(len(remains)):    dfs(path + [remains[i]], remains[:i] + remains[i+1:])
# 套模板def dfs(pth,idx):    if idx == len(ds):        res.append(pth)        return    for c in dic[ds[idx]]:        dfs(pth + c, idx + 1)
```
**「多重限制」**第 37 题 解数独 | 第 51 题 N皇后
```
# 多重限制def backtrack(pos):  if pos == n:    return True  i, j = empty[pos]  for num in row[i] & col[j] & block[bidx(i, j)]:    row[i].remove(num)    col[j].remove(num)    block[bidx(i, j)].remove(num)    board[i][j] = str(num)    if backtrack(pos + 1): return True    row[i].add(num)    col[j].add(num)    block[bidx(i, j)].add(num)
```
**「递归」**第 10 题 正则匹配
# 递归def isMatch(self, s: str, p: str) -> bool:  if not p:     return not s  f = bool(s and p[0] in {s[0],'.'})  if len(p) >= 2 and p[1] == "*":    return self.isMatch(s, p[2:]) or f and self.isMatch(s[1:], p)  else:    return f and self.isMatch(s[1:], p[1:])
【并查集模板】
```
#虚拟节点用以连接某一特征的全部节点，类似于链表的preHeaddummy parent = {}size = collections.defaultdict(lambda:1)cnt = 0def find(x):    parent.setdefault(x,x)    while x != parent[x]:        x = parent[x]        #路径压缩 parent[x] = parent[parent[x]];    return xdef union(x,y):    nonlocal cnt    if connected(x,y): return    # 小的树挂到大的树上， 使树尽量平衡    xP = find(x)    yP = find(y)    if size[hP] < size[yP]:        parent[xP] = yP    else:        parent[yP] = xP    size[xP] += size[yP]    # 优化结束    parent[find(x)] = find(y)    # 不优化    cnt -= 1    return size[xP]def connected(x, y):    return find(x) == find(y)def add(self,x):    if x not in parent:        parent[x] = None        cnt += 1# 检查是否有环for a, b in edges:    if connected(a, b):         return True    union(a, b)# 将每个集合组成以头为key的字典res = collections.defaultdict(list)for e in e2n:    res[uf.find(e)].append(e)
```
【拓扑排序模板】
```
# 【拓扑排序模板】ins = [0] * nous = collections.defaultdict(list)for cur, pre in ps:    ins[cur] += 1              #入度    ous[pre].append(cur)    #出度res = list(filter(lambda x:ins[x]==0, range(n)))q = collections.deque(res)while q:    pre = q.popleft()    for cur in ous[pre]:   #释放出度队列        ins[cur] -= 1        if not ins[cur]:             q.append(cur)  #入度为0解锁            res.append(cur)
```
【单调栈模板】
```
# s中一般存索引for i in range(len(ns):    while stack and ns[stack[-1]] <= ns[i]: # 单调递减栈        stack.pop()    # 业务逻辑    stack.append(i)
```
**「单调递增」**第 84 题 求最大矩形
```
# 第 **84** 题 求最大矩形for i in range(len(hs)):    while s and hs[i] < hs[s[-1]]:        base = s.pop()        if s:            H = hs[base]            W = i - s[-1] - 1 # 当前弹出的做高，当前与次小做宽            res = max(res, H * W)    s.append(i)
```
**「单调递增,考虑剩余」**第 316 题 去除重复字符
```
# 第 **316** 题 去除重复字符for i,c in enumerate(ss):    if c not in s:        while s and c < s[-1] and s[-1] in ss[i:]:            s.pop()        s.append(c)
```
**「单调递减」**第 42 题 接雨水
```
# 第 **42** 题 接雨水for i in range(len(hgt)):    while stack and hgt[i] > hgt[stack[-1]]: #递减栈        base = stack.pop()        if stack:            LH = hgt[stack[-1]]            W = i - stack[-1] - 1            H = min(LH,hgt[i]) - hgt[base]            res += W * H     stack.append(i)
```
**「单调递减」**第 739 题 每日温度
```
# 第 **739** 题 每日温度for i in range(len(T)-1,-1,-1):    while s and T[s[-1]] <= T[i] :   #递减栈        s.pop()    res[i] = s[-1] - i if s else 0    s.append(i)
```
【二分模板】
# 1355579 T=5 => 13(5)55579 返回2# ps[i-1] < ps[i] <= ps[i+1]bisect.bisect_left(ps, T, L=0, R=len(ns))  # 1355579 T=5 => 13555(5)79 返回5# ps[i-1] <= ps[i] < ps[i+1]bisect.bisect_right(ps, T, L=0, R=len(ns))  bisect.bisect(ps, T, L=0, R=len(ns))   
**「中位返回」**第 33 题 搜索旋转排序数组 | 第374题 猜数字大小 | 第69题 x平方根
# 中位返回while L <= R:    M = (L + R) // 2    if nums[M] == T:        return M    elif nums[M] < T:        L = M + 1    else:        R = M - 1
**「区域压缩」**第278题 第一个错误版本| 第162题 寻找峰值 | 第153题 寻找数组最小值
# 区域压缩while L < R:    M = (L + R) // 2    if need in s[L:M]:        R = M    else:        L = M + 1
【动态规划模板】

**「单串问题」**

- 70 爬楼梯问题
- 801 使序列递增的最小交换次数
- 746 使用最小花费爬楼梯
- 300 最长上升子序列

# 依赖前单个元素dp[i] = dp[i-1] + ns[i]# 依赖前部区域元素for i in range(n)    for j in range(i)        dp[i] = min(dp[i], f(dp[j])

**「单串加状态问题」**

- 887 鸡蛋掉落

# 鸡蛋掉落while cur[K] < N:             # 还剩 j 个蛋 测 ans 次 覆盖多少层    for j in range(1, K + 1): # 覆盖总层数 碎了 -1 次层数 + 1 + 没碎 -1 次层数        cur[j] = prev[j - 1] + 1 + prev[j]    ans += 1    prev = copy.deepcopy(cur)

- 813 最大平均值分组

# 813 最大平均值分组for k in range(K-1):            #循环k次    for i in range(N):          #每次均依赖上次的结果        for j in range(i+1, N):            dp[i] = max(dp[i], avrg(i, j) + dp[j])

- 410 分割数组最大值

# 410 分割数组最大值for k in range(1,K):    for i in range(N):         for j in range(i):            # 0~i中分 k 段最大 即为            # 0~j中分k-1段最大 和 j到i的前缀和的最大            dp[i][k] = min(dp[i][k], max(dp[j][k-1], ps[i+1] - ps[

**「经典双串LCS问题」**
# 经典双串LCS问题dp = [[0] * (M+1) for _ in range(N+1)]for i in range(N):    for j in range(M):        if t1[i] == t2[j] : dp[i+1][j+1] = dp[i][j] + 1         else : dp[i+1][j+1] = max(dp[i][j+1],dp[i+1][j])

**「区间动态规划」**

- 5 最长回文子串
- 647 最多回文子串
- 516 最长回文子序列
- 1312 最长回文插入次数

# dp[i][j] 代表从 i 到 j 的最长子串满足条件的数量# i-- < j++  ==> i 在 0~j 范围内 --dp = [[0] * (N) for _ in range(N)]for j in range(N):    dp[j][j] = 1    for i in range(j-1,-1,-1):        if ss[i] == ss[j]:            dp[i][j] = dp[i+1][j-1] +2        else :            dp[i][j] = max(dp[i+1][j],dp[i][j-1])

**「区间分治动态规划」**
486 预测赢家：https://leetcode-cn.com/problems/predict-the-winner/?spm=ata.21736010.0.0.49ae7ec0sfNWbz
312 戳气球：https://ata.atatech.org/articles/***https://leetcode-cn.com/problems/burst-balloons/***?spm=ata.21736010.0.0.49ae7ec0sfNWbz
664 奇怪的打印机：https://ata.atatech.org/articles/***https://leetcode-cn.com/problems/strange-printer/***?spm=ata.21736010.0.0.49ae7ec0sfNWbz
546 移除盒子：https://ata.atatech.org/articles/***https://leetcode-cn.com/problems/remove-boxes/***?spm=ata.21736010.0.0.49ae7ec0sfNWbz
```
# 区间分治动态规划def helper(self, ns: List[int]) :    N = len(ns)    dp = [[0] * N for _ in range(N+1)]    for l in range(N): # 长度从小到大        for i in range(N-l): # 以 i 为 开头            j = i + l           # 以 j 为 终点            for k in range(i,j): # 以 k 为分割点，进行分治                         // Todo 业务逻辑
```
**「卡特兰数」**
# 卡特兰数g(n) = g(0)*g(n-1) + g(1)*g(n-2) ...g(n-1)*g(0)dp=[1] + [0] * nfor i in range(1,n+1):    for j in range(1,i+1):        dp[i] += dp[j-1] * dp[i-j]
【滑动窗口】
```
"""给定待查串s和目标串t"""nd, wd = {}, {}nd = collections.Counter(s1)L, R = 0, 0cnt = 0 # 满足条件个数while R < len(s):        # 窗口右边界不断扩大，本质是搜索问题的可能解    c = s[R]      # 即将加入到窗口中的字符    R += 1    更新窗口中的数据    while 满足窗口收缩条件：  # 窗口的左边界收缩，本质是优化可行解        记录或返回结果        d = s[L]   # 即将从窗口中删除的字符        L += 1        更新窗口中的数据return 结果
# 固定窗口 ,比滑动窗口更快一些i = j = cnt = 0      for j in range(len(A)):    if A[j] == 0:         cnt += 1    if cnt > K: #不满足时 平移        if A[i] == 0:            cnt -= 1        i += 1return j - i + 1         for j in range(len(A)):    if A[j] == 0:        cnt += 1    while cnt > K:        if A[i] == 0:            cnt -= 1        i += 1    res = max(res, j - i + 1)return res
```
【前缀和】
**「累加和存位置」**
1371 最长偶数元音子数组
525 最长相等01子数组
325 最长和为k 子数组
# 前缀和初始化psd = {0: -1}  for i in range(len(s)):    t ^= cd.get(s[i], 0) # 业务逻辑    if t not in psd:        psd[t] = i       # 第一次存入数组    else:        ans = max(ans, i - psd[t]) #已存入则开始计算
**「累加和存数量」**
560 和为K的子数组数量
统计优美子数组
# 累加和存数量psd = {0:1}for i in range(len(ns)):    s += ns[i]    if s - T in psd:        ans += psd[s - T] # 存数量    psd[s] = psd.get(s,0) + 1
**「模K状态前缀和」**
523 连续和为 k 倍 的子数组（存索引）
974 和被k 整除 子数组数量（存数量）
# 模K状态前缀和psd = {0:-1}ans = s = 0for i in range(len(ns)):    s += ns[i]                # 业务逻辑    if T != 0: s %= abs(T)    # 模k状态做key，索引做值    if s not in psd:        psd[s] = i    elif i - psd[s] > 1:        return True
**「矩阵前缀和」**

- 363 不超过K的最大数值和
- 1074 和为目标值的子矩阵数量

# 矩阵前缀和for i in range(m):        #固定左边界    ps = [0] * n    for j in range(i, m): #固定右边界        psS = 0            dct = {0:1}       #初始只有一种可能        for k in range(n): # 以高做前缀和            ps[k] += mtx[j][k]          # 每行前缀和            psS += ps[k]                # n行前缀和            cnt += dct.get(psS - T, 0)  # 满足条件cnt            dct[psS] = dct.get(psS,0) + 1 # 保存当前状态return cnt
【双指针】
# 双指针def removeElement(self, ns: List[int], val: int) -> int:    slow = 0    n = len(ns)    for fast in range(n):        if ns[fast] != val:            ns[slow] = ns[fast]            slow += 1    return slow
【深度优先】
**「二叉树遍历模板」**

```
# 递归# 时间复杂度：O(n)，n为节点数，访问每个节点恰好一次。# 空间复杂度：空间复杂度：O(h)，h为树的高度。最坏情况下需要空间O(n)，平均情况为O(logn)
# 递归1：二叉树遍历最易理解和实现版本class Solution:    def preOrd(self, root: TreeNode) -> List[int]:        if not root:            return []        # 前序递归        return [root.val] + self.preOrd(root.left) + self.preOrd(root.right)        # # 中序递归         # return self.inOrd(root.left) + [root.val] + self.inOrd(root.right)        # # 后序递归        # return self.postOrd(root.left) + self.postOrd(root.right) + [root.val]
# 递归2：通用模板，可以适应不同的题目，添加参数、增加返回条件、修改进入递归条件、自定义返回值class Solution:    def preOrd(self, root: TreeNode) -> List[int]:        def dfs(cur):            if not cur:                return                  # 前序递归            res.append(cur.val)            dfs(cur.left)            dfs(cur.right)             # # 中序递归            # dfs(cur.left)            # res.append(cur.val)            # dfs(cur.right)            # # 后序递归            # dfs(cur.left)            # dfs(cur.right)            # res.append(cur.val)              res = []        dfs(root)        return res

# 迭代# 时间复杂度：O(n)，n为节点数，访问每个节点恰好一次。# 空间复杂度：O(h)，h为树的高度。取决于树的结构，最坏情况存储整棵树，即O(n)# 迭代1：前序遍历最常用模板（后序同样可以用）class Solution:    def preOrd(self, root: TreeNode) -> List[int]:        if not root:            return []                res = []        stack = [root]        # # 前序迭代模板：最常用的二叉树DFS迭代遍历模板        while stack:            cur = stack.pop()            res.append(cur.val)            if cur.right:                stack.append(cur.right)            if cur.left:                stack.append(cur.left)        return res                # # 后序迭代，相同模板：将前序迭代进栈顺序稍作修改，最后得到的结果反转        # while stack:        #     cur = stack.pop()        #     if cur.left:        #         stack.append(cur.left)        #     if cur.right:        #         stack.append(cur.right)        #     res.append(cur.val)        # return res[::-1]
# 迭代1：层序遍历最常用模板class Solution:    def levelOrder(self, root: TreeNode) -> List[List[int]]:        if not root:            return []        q = deque([root])        res = []        while q :            l = []            for i in range(len(q)) :                t = q.popleft()                l.append(t.val)                if t.left : q.append(t.left)                if t.right : q.append(t.right)            res.append(l)        return res
        # 迭代2：前、中、后序遍历通用模板（只需一个栈的空间）class Solution:    def inOrd(self, root: TreeNode) -> List[int]:         res = []        stack = []        cur = root        # 中序，模板：先用指针找到每颗子树的最左下角，然后进行进出栈操作        while stack or cur:            while cur:                stack.append(cur)                cur = cur.left            cur = stack.pop()            res.append(cur.val)            cur = cur.right        return res                # # 前序，相同模板        # while stack or cur:        #     while cur:        #         res.append(cur.val)        #         stack.append(cur)        #         cur = cur.left        #     cur = stack.pop()        #     cur = cur.right        # return res                # # 后序，相同模板        # while stack or cur:        #     while cur:        #         res.append(cur.val)        #         stack.append(cur)        #         cur = cur.right        #     cur = stack.pop()        #     cur = cur.left        # return res[::-1]        
# 迭代3：标记法迭代（需要双倍的空间来存储访问状态）：# 前、中、后、层序通用模板，只需改变进栈顺序或即可实现前后中序遍历，# 而层序遍历则使用队列先进先出。0表示当前未访问，1表示已访问。class Solution:    def preOrd(self, root: TreeNode) -> List[int]:        res = []        stack = [(0, root)]        while stack:            flag, cur = stack.pop()            if not cur: continue            if flag == 0:                # 前序，标记法                stack.append((0, cur.right))                stack.append((0, cur.left))                stack.append((1, cur))                                # # 后序，标记法                # stack.append((1, cur))                # stack.append((0, cur.right))                # stack.append((0, cur.left))                                # # 中序，标记法                # stack.append((0, cur.right))                # stack.append((1, cur))                # stack.append((0, cur.left))              else:                res.append(cur.val)          return res                # # 层序，标记法        # res = []        # queue = [(0, root)]        # while queue:        #     flag, cur = queue.pop(0)  # 注意是队列，先进先出        #     if not cur: continue        #     if flag == 0:                  # 层序遍历这三个的顺序无所谓，因为是队列，只弹出队首元素        #         queue.append((1, cur))        #         queue.append((0, cur.left))        #         queue.append((0, cur.right))        #     else:        #         res.append(cur.val)        # return res


# 莫里斯遍历# 时间复杂度：O(n)，n为节点数，看似超过O(n)，有的节点可能要访问两次，实际分析还是O(n)# 空间复杂度：O(1)，如果在遍历过程中就输出节点值，则只需常数空间就能得到中序遍历结果，空间只需两个指针。# 如果将结果储存最后输出，则空间复杂度还是O(n)。
# PS：莫里斯遍历实际上是在原有二叉树的结构基础上，构造了线索二叉树，# 线索二叉树定义为：原本为空的右子节点指向了中序遍历顺序之后的那个节点，把所有原本为空的左子节点都指向了中序遍历之前的那个节点
# 此处只给出中序遍历，前序遍历只需修改输出顺序即可# 而后序遍历，由于遍历是从根开始的，而线索二叉树是将为空的左右子节点连接到相应的顺序上，使其能够按照相应准则输出# 但是后序遍历的根节点却已经没有额外的空间来标记自己下一个应该访问的节点，# 所以这里需要建立一个临时节点dump，令其左孩子是root。并且还需要一个子过程，就是倒序输出某两个节点之间路径上的各个节点。
# 莫里斯遍历，借助线索二叉树中序遍历（附前序遍历）class Solution:    def inOrd(self, root: TreeNode) -> List[int]:        res = []        # cur = pre = TreeNode(None)        cur = root
        while cur:            if not cur.left:                res.append(cur.val)                # print(cur.val)                cur = cur.right            else:                pre = cur.left                while pre.right and pre.right != cur:                    pre = pre.right                if not pre.right:                    # print(cur.val) 这里是前序遍历的代码，前序与中序的唯一差别                    pre.right = cur                    cur = cur.left                else:                    pre.right = None                    res.append(cur.val)                    # print(cur.val)                    cur = cur.right        return res

# N叉树遍历# 时间复杂度：时间复杂度：O(M)，其中 M 是 N 叉树中的节点个数。每个节点只会入栈和出栈各一次。# 空间复杂度：O(M)。在最坏的情况下，这棵 N 叉树只有 2 层，所有第 2 层的节点都是根节点的孩子。# 将根节点推出栈后，需要将这些节点都放入栈，共有 M−1个节点，因此栈的大小为 O(M)。

# N叉树简洁递归class Solution:    def preorder(self, root: 'Node') -> List[int]:        if not root: return []        res = [root.val]        for node in root.children:            res.extend(self.preorder(node))        return res
# N叉树通用递归模板class Solution:    def preorder(self, root: 'Node') -> List[int]:        res = []        def helper(root):            if not root:                return            res.append(root.val)            for child in root.children:                helper(child)        helper(root)        return res
# N叉树迭代方法class Solution:    def preorder(self, root: 'Node') -> List[int]:        if not root:            return []        s = [root]        # s.append(root)        res = []        while s:            node = s.pop()            res.append(node.val)            # for child in node.children[::-1]:            #     s.append(child)            s.extend(node.children[::-1])        return res
```
【广度优先】
```
# 「**无向图的遍历**」q = collections.deque([i])while q:    cur = q.popleft()    for nxt in dt[cur]:        if not vst[nxt]:            vstd[nxt] = True            q.append(nxt)
```
# 「**二叉树层序遍历**」q = deque([root])res = []while q :    l = []    for i in range(len(q)) :        t = q.popleft()        l.append(t.val)        if t.left : q.append(t.left)        if t.right : q.append(t.right)    res.append(l)return res
【图论】
```
#「Dijkstra最短路径」dic = collections.defaultdict(list)for u, v, w in edges:    dic[u].append([v, w])    dic[v].append([u, w])q = [(0, n)]dist = [-1] * (n + 1)while q:    dis, cur = heapq.heappop(q)    if dist[cur] < 0:        dist[cur] = dis        for nxt, wi in dic[cur]:            heapq.heappush(q, [dis + wi, nxt])
```
**「Floyd 求图中路径」**
# Floyd算法 求图中任意2点距离ds = defaultdict(int)st = set()for i, (x, y) in enumerate(ess):    ds[(x, y)] = vs[i]    ds[(y, x)] = 1 / vs[i]    st.update({x,y})arr = list(st)for k in arr:    for i in arr:        for j in arr:            if ds[(i, k)] and ds[(k, j)]:                ds[(i, j)] = ds[(i, k)] * ds[(k, j)]


> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/rmwkooukymzcgygp>