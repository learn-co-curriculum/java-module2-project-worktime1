# Module2 Project Worktime - Concert Class

## Learning Goals

- Spend some time working on your project.
- Implement a `Concert` class with fields, a constructor, and
  methods to access and mutate the fields.

## Introduction

The instructions for task#1 are contained in the [Module2 Project on Github](https://github.com/learn-co-curriculum/java-module2-project),
and are repeated here as part of this project worktime lesson.

Now that we have learned about Java constructors and methods, it is time to
apply this new knowledge to our project!

If you have not already done so, you should fork
and clone [Module2 Project on Github](https://github.com/learn-co-curriculum/java-module2-project).

The starter code contains several empty classes that
you will develop incrementally as you learn the material
in this module.

![uml module2 project](https://curriculum-content.s3.amazonaws.com/6676/java-multipleclasses/uml_module2_project.png)

## Task #1 - `Concert` Class

The `Concert` class encapsulates data about:
- the artist performing at a music concert
- the number of tickets available for purchase
- the number of people on the wait list

(1) Add instance variables in the following order to the `Concert` class:

- A String named `performer`.
- An int named `available`.
- An int named `waitlist`.

(2) Add a constructor that takes two parameters to initialize the `performer` and
`available` instance variables.  The `waitlist` instance variable
should be initialized to a default value of 0.

(3) Use IntelliJ to generate getter methods for each of the instance variables.

(4) Use IntelliJ to generate a `toString()` method, selecting all fields.

(5) Edit the `ConcertTest` Junit test class to test the constructor, getters,
and `toString` methods:

```java
class ConcertTest {

  private Concert c1, c2;

  @BeforeEach
  void setup() {
    c1 = new Concert("The Weeknd", 10);
    c2 = new Concert("Harry Styles", 2);
  }

  @Test
  void constructor() {
    assertEquals("The Weeknd", c1.getPerformer());
    assertEquals(10, c1.getAvailable());
    assertEquals(0, c1.getWaitlist());

    assertEquals("Harry Styles", c2.getPerformer());
    assertEquals(2, c2.getAvailable());
    assertEquals(0, c2.getWaitlist());
  }

  @Test
  void testToString() {
    assertEquals("Concert{performer='The Weeknd', available=10, waitlist=0}", c1.toString());
    assertEquals("Concert{performer='Harry Styles', available=2, waitlist=0}", c2.toString());
  }

}
```

Run the Junit tests to ensure the code passes the tests.

Once you have that working, edit the `Concert` class to add the following methods:

- A method named `purchaseTicket()` that takes no parameters and returns a `boolean`.
    - If the number of available tickets is positive, decrement the number
      of available tickets by 1 and return `true`.  Return `false` if there are
      no tickets available.
- A method named `addtoWaitList()` that takes no parameters and does not return a value.
    - Increment the `waitlist` value by 1.

Edit the `ConcertTest` Junit test class to add the following test methods.

```java
@Test
void purchaseTicket() {
    assertEquals(10, c1.getAvailable());
    assertTrue(c1.purchaseTicket());
    assertEquals(9, c1.getAvailable());
    assertTrue(c1.purchaseTicket());
    assertEquals(8, c1.getAvailable());

    assertEquals(2, c2.getAvailable());
    assertTrue(c2.purchaseTicket());
    assertEquals(1, c2.getAvailable());
    assertTrue(c2.purchaseTicket());
    assertEquals(0, c2.getAvailable());
    //no tickets left, remain at 0
    assertFalse(c2.purchaseTicket());
    assertEquals(0, c2.getAvailable());
    }

@Test
void addToWaitlist() {
    assertEquals(0, c1.getWaitlist());
    c1.addToWaitlist();
    assertEquals(1, c1.getWaitlist());
    c1.addToWaitlist();
    assertEquals(2, c1.getWaitlist());

    assertEquals(0, c2.getWaitlist());
    c2.addToWaitlist();
    assertEquals(1, c2.getWaitlist());
    c2.addToWaitlist();
    assertEquals(2, c2.getWaitlist());
    }
```

