## This is just some notes for who want to get Ruby Certificate

#### 1. Identify

- 0..9
- A-Z, a-z
- underscore
- Number is not placed in the first
- Do not same with key of Ruby

- Example for wrong identify:
  - 1_to_100
  - abc?
  - abc-1

#### 2. Scope of variable, constant

 Type           | Identify rules                           | Scope                                        | Value when do not init                     |
 -------------- | ---------------------------------------- | -------------------------------------------- | ------------------------------------------ |
 Local variable | First character: alphabeta or underscore | The nearest scope(where variable is defined) | If defined -> nil, else -> raise exception
Global variable | First character: $ | All | nil
Class variable | First character: @@ | All instances of class can see | raise exception
Instance variable | First character: @ | Only in that instance | nil
Constant | First character: Must be upcase | | raise exception

- Example for scope of variable, constant:
  - Local variable:
    ```
    foo = 1
    def call_variable
      puts foo
    end
    call_variable -> raise exception
    ```
  - Global variable:
    ```
    $foo = 1
    def call_variable
      puts $foo
    end
    call_variable -> 1
    ```
  - Class variable:
    ```
    class Test
      @@class_var_1 = 100
      def instance_method_call_defined_variable
        puts @@class_var_1
      end
      def instance_method_call_undefined_variable
        puts @@class_var_2
      end
      class << self
        def instance_method_call_undefined_variable
          puts @@class_var_1
        end
      end
    end
    Test.new.instance_method_call_defined_variable → 100
    Test.new.instance_method_call_undefined_variable → raise exception
    Test.class_method_call_defined_variable → 100
    ```
  - Constant:
    ```
    module TestConstant
      TEST_CONSTANT = 1

      def instance_call_constant
        puts TEST_CONSTANT
      end

      class << self
        def class_call_constant
          puts TEST_CONSTANT
        end
      end
    end

    class TestConstantClass
      include TestConstant
    end

    TestConstantClass.class_call_constant → raise exception
    TestConstant.class_call_constant → 1
    TestConstantClass.new.instance_call_constant → 1
    TestConstantClass::TEST_CONSTANT → 1
    TestConstant::TEST_CONSTANT → 1
    ```