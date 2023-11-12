# Software Certification PW Report

### 1.a and 1.b
```
swich age:
  case >=6:        valid
  case >=0 and <6: valid
  case < 0:        invalid

switch goodHealth:
  case 0:          valid
  case 1:          valid
  case <0:         invalid
  case >1:         invalid

switch hasNoVaccine:
  case 0:          valid
  case 1:          valid
  case <0:         invalid
  case >1:         invalid
```

### 1.c
Test values:
- Age: -1, 0, 5, 6
- Health: -1, 0, 1, 2
- hasNoVaccine: -1, 0, 1, 2

### 2.a
```[Elshad's code goes here]```

### 2.b
![img](./IMG/Untitled.jpg)
![img](./IMG/Untitled1.jpg)
![img](./IMG/Untitled3.jpg)
![img](./IMG/Untitled4.jpg)

### 2.c
90%

### 3.a
```
Age boundary analysis:
[...-1][0...5][6...]
```

### 5.a
| Conditions  |  Test1  |  Test2  |  Test3  |  Test4  |  Test5  |  Test6  |  Test7  |  Test8  |  Test9  |  Test10 |  Test11 |  Test12 |  Test13 |  Test14 |  Test15 |  Test16 |
|------------ |---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|
| age >=0     |    T    |    T    |    T    |    T    |    T    |    T    |    T    |    T    |    F    |    F    |    F    |    F    |    F    |    F    |    F    |    F    |
| age >=6     |    T    |    T    |    F    |    T    |    T    |    F    |    F    |    F    |    T    |    T    |    F    |    T    |    T    |    F    |    F    |    F    |
| goodHealth  |    T    |    T    |    T    |    F    |    F    |    T    |    F    |    F    |    T    |    T    |    T    |    F    |    F    |    T    |    F    |    F    |
| noVaccine   |    T    |    F    |    T    |    T    |    F    |    F    |    T    |    F    |    T    |    F    |    T    |    T    |    F    |    F    |    T    |    F    |
| Result      |    T    |    F    |    F    |    F    |    F    |    F    |    F    |    F    |   -1    |   -1    |   -1    |   -1    |   -1    |   -1    |   -1    |   -1    |

### 4.a 
- No

### 5.b
| Conditions  |  Test1  |  Test5  |  Test8  |  Test9  |
|------------ |---------|---------|---------|---------|
| age >=0     |    T    |    T    |    T    |    F    |
| age >=6     |    T    |    T    |    F    |    T    |
| goodHealth  |    T    |    F    |    F    |    T    |
| noVaccine   |    T    |    F    |    F    |    T    |
| Result      |    T    |    F    |    F    |   -1    |

### 6.a
![img](./IMG/unt6.jpeg)

### 7.a
100% coverage<br>
![img](./IMG/unt5.jpeg)


### 8.a:
3IF + 1 = 4

### 9.a:
2^4 = 16;
4 => conditions

### 10.a:
No only MC/DC Decision and statement covarages used.

### 11.a
- Modified condition / decision coverage
- Functional coverage

### 12.a:
According to the DO-178B standard Decision and Statement coverage shoudl used.

### 13.a
Yes, MCDC coverage is 100% for line 10, because there is only one condition is the decision both True and False has been tested by running Test1 and Test8

### 14.a:
Integration test

### 15.a
```
#include <stdio.h>
#include <stdint.h>
#include <stdarg.h>
#include <stddef.h>
#include <setjmp.h>
#include "cmocka.h"
#include <string.h>
#include "compute.h"

#define true 1
#define false 0
/* A test case that does nothing and succeeds. */
// declaration du mock
void recupLimitAge(int* ageLimit){
  function_called();
  *ageLimit = (int)mock();
}
/* A test case that does nothing and succeeds. */
static void null_test_success(void **state){
  (void) state;
}
static void below_zero_success(){
  int age=-1; int goodHealth=1; int hasNoVaccine=1; int timesCount=1;
  expect_function_calls(recupLimitAge, timesCount);
  will_return(recupLimitAge, 6);
  assert_int_equal(computeVaccine(age, goodHealth, hasNoVaccine), -1);
}

int main(void){
  const struct CMUnitTest tests[]={
    cmocka_unit_test(null_test_success),
    cmocka_unit_test(below_zero_success),
  };
  printf("recupLimitAge been called: %d\n");
  return cmocka_run_group_tests_name("toto",tests, NULL, NULL);
}
```

### 16.a:
In our code we use mock to simulate function, because we don't have corresponding function.
in general mocking used to simulate networks, functions, hardware, databases etc.

### 17.a:
Low Module computeVaccine uses module age.h's function to compute ageLimit

### 18.a:
There is not enough comment. First time when i wanted to understand code, I faced with difficulties
Unused variable. response variable never used.
Use of magic number instead of constants. Code returns magic numbers like -1, 0, 1, we can define this numbers before hand then use them. For example: define INVALID_Value -1; define APPROPRIATE 1; NOT_APPROPRIATE 0

### 19.a
- Low level components being untested means its harder to find cause of high level components failing tests (and debug them) due to errors in many untested low level code.
- High level components being untested means lower confidence in software quality in general because often high level components are often user-facing, so obvious bugs on user side will go untested.
- Untested code at all levels means undetected, user-facing bugs will pop-up in production.

### 20.a:
Instrumentation is used to monitor or measure the level of a product's performance, to diagnose errors and to write trace information. It is used to track which parts of the code that were executed during testing, to track if test fails of succeeds and to measure test coverage.

### 21.a
Unit Test Layer
