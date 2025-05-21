# Write a verilog code to generate the ramdom number and sort them in ascending order
```
// Code your testbench here
// or browse Examples
module random_unique_tb;

  integer rand_nums[0:9];     // Array to store 10 unique random numbers .
  integer i, j;               //one for to maintain num less than 10, another for comaparing with previous .
  integer temp;
  bit is_unique;              // decision maker .

  initial begin
    i = 0;
    while (i < 10) begin
      temp = $random % 100;  // Generate random number between 0 and 99
      
          is_unique = 1;

      // Check if the number already exists
      for (j = 0; j < i; j = j + 1) begin
        if (rand_nums[j] == temp) begin
          is_unique = 0;
          break;
        end
      end

      // If number is unique, store it
      if (is_unique) begin
        rand_nums[i] = temp;
        i = i + 1;
      end
    end

    // Bubble Sort: sort array in ascending order
    for (i = 0; i < 9; i = i + 1) begin
      for (j = 0; j < 9 - i; j = j + 1) begin
        if (rand_nums[j] > rand_nums[j + 1]) begin
          temp = rand_nums[j];
          rand_nums[j] = rand_nums[j + 1];
          rand_nums[j + 1] = temp;
        end
      end
    end

    // Display the sorted random numbers
    $display("10 Unique Random Numbers in Ascending Order:");
    for (i = 0; i < 10; i = i + 1) begin
      $display("%0d: %0d", i, rand_nums[i]);
    end

    $finish;
  end

endmodule
```
# NOTE 
```
1.Use bubble sort algorithm.
```
# OUTPUT
![image](https://github.com/user-attachments/assets/88f378e2-55b1-43f6-a818-c5abc5f1edb4)



