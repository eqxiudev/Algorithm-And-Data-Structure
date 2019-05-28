#Queue
###1、数组的实现
class ArrayQueue {
    int count;
    String[] queue;
    int head;
    int tail;

    public ArrayQueue(int capcity) {
        count = capcity;
        queue = new String[count];
        head = 0;
        tail = 0;
    }

    public boolean enqueue(String elem) {
        // 队列满了
        if (count == tail) {
            return false;
        }
        queue[tail] = elem;
        tail++;
        return true;
    }

    public String dequeue() {
        if (head == tail) {
            return null;
        }
        String value = queue[head];
        head++;
        return value;
    }
}


###2、环形
class CirQueue {
    int count;
    String[] queue;
    int head;
    int tail;

    public CirQueue(int capcity) {
        count = capcity;
        queue = new String[count];
        head = 0;
        tail = 0;
    }

    public boolean enqueue(String elem) {
        // 队列满了
        if ((tail + 1) % count == head) {
            return false;
        }
        queue[tail] = elem;
        tail = (tail + 1) % count;
        return true;
    }

    public String dequeue() {
        if (head == tail) {
            return null;
        }
        String value = queue[head];
        head = (head + 1) % count;
        return value;
    }
}
