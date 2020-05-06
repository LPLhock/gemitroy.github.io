# Thread Safe Stack

### Solution A

```text
public class TSStack {
    private static final int capacity = 8;
    private int top = -1;
    private int[] stack = new int[capacity];
    
    public synchronized void push(Integer n) {
        while ((top + 1) == capacity) {
            try {
                wait();
            } catch(InterruptedException e) {}
        }
        stack[++top] = n;
        notifyAll();
    }
    
    public synchronized Integer pop() {
        while (top < 0) {
            try {
                wait();
            } catch(InterruptedException e) {}
        }
        top--;
        notifyAll();
        return stack[top];        
    }
```

