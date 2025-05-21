# Write a verilog code to generate a random number with in a range of -99 to +99
```
module random_unique_tb;

  integer rand_nums[0:9];     // Array to store 10 unique random numbers
  integer i, j;
  integer temp;
  bit is_unique;

  initial begin
    i = 0;
    while (i<10) begin
      temp = $random%100;  // Generate random number between 0 and 99
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

    // Display the generated unique random numbers
    $display("10 Unique Random Numbers:");
    for (i = 0; i < 10; i = i + 1) begin
      $display("%0d: %0d", i, rand_nums[i]);
    end
 end

endmodule
```
# NOTE 
```
1. To fix the range a=random%N is used .It will print the values from -(N-1) to (N-1).
```
# OUTPUT 

![Screenshot (496)](https://github.com/user-attachments/assets/6de8bff7-fdac-4861-9954-dd799e09d130)
