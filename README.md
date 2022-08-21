# leetcode---225

https://www.youtube.com/watch?v=rW4vm0-DLYc&list=PLWHz3Jit5jysxX-uyqwSZ1_nBw50EVuNz&index=15

use queue method to realize stack:


            class MyStack:

                def __init__(self):
                    self.q = deque()
                    # same as the old

                def push(self, x: int) -> None:
                    self.q.append(x)
                    # add is the same

                def pop(self) -> int:
                    for i in range(len(self.q)-1):
                        self.push(self.q.pop())
                    return self.q.pop()
                      # 【1，2，3，4，5】  pop（）是把最后一个删除，同时返回剩余
                      # 【5，1，2，3，4】  在queue里面把前面的都删除，加到后面去。同时返回后面的
                      # 为了保证是最后一个，所以loop只到 n-1

                def top(self) -> int:
                    return self.q[-1]
                    # top would be the last one

                def empty(self) -> bool:
                    return len(self.q) == 0
                    # if the length is 0, return True

2）用空集来写：
记得拿空桶子来装 —— lastValue，这样，后来改变list本身也不受影响

                        class MyStack:

                            def __init__(self):
                                self.stack = []

                            def push(self, x: int) -> None:
                                self.stack.append(x)

                            def pop(self) -> int:
                                lastIndex = len(self.stack) - 1 
                                lastValue = self.stack[-1]
                                newStack = []
                                for i in range(len(self.stack)-1):
                                    newStack.append(self.stack[i])
                                    print(lastValue)

                                self.stack = newStack
                                return lastValue

                            def top(self) -> int:
                                return self.stack[-1]

                            def empty(self) -> bool:
                                return self.stack == []


                        # Your MyStack object will be instantiated and called as such:
                        # obj = MyStack()
                        # obj.push(x)
                        # param_2 = obj.pop()
                        # param_3 = obj.top()
                        # param_4 = obj.empty()
