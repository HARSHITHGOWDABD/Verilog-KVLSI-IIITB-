# Write a verilog code to generate 10 unique random number  
```
module random_unique_tb;

  integer rand_nums[0:9];     // Array to store 10 unique random numbers
  integer i, j;
  integer temp;
  bit is_unique;

  initial begin
    i = 0;
    while (i < 10) begin             // helps to limit 10 number 
      temp = $random;  // Generate random number between 0 and 99
      is_unique = 1;

      // Check if the number already exists
      for (j = 0; j < i; j = j + 1) begin    // helps to avoid repetation
        if (rand_nums[j] == temp) begin      // compare with previous value 
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

    $finish;
  end

endmodule
```
# OUTPUT 
![Screenshot (496)](https://github.com/user-attachments/assets/99292296-138c-4491-8b24-fafc8d53c0a8)



