
public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1 allocate and initialize memory in stack
        Object o = new Object();        // 2 class loading Object
                                        //   allocate memory in heap, add reference to stack
        Integer ii = 2;                 // 3 class loading Integer
                                        //   allocate memory in heap, add reference to stack,
                                        //   object initialization by reference
        printAll(o, i, ii);             // 4 put method main on the run queue,
                                        //   pass control to the method printAll
                                        //   waiting for the printAll() to complete
                                        //   dequeuing a method main
        System.out.println("finished"); // 7 put method main on the run queue,
                                        //   allocate memory for string in heap
                                        //   pass control to the method println()
                                        //   waiting for the println() to complete
                                        //   dequeuing a method main
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;       // 5 allocate memory in heap, add reference to stack,
                                        //   object initialization by reference
                                        // а может компилятор умный и не создаст ничего...
System.out.println(o.toString() + i + ii);  // 6
    }
}
