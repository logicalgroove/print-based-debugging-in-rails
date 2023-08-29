## Print Based Rails debugging

Print-based debugging is all about making your log messages stand out and being easily digestible. Here are some less common but potentially helpful hacks and tips for debugging.

1. **Custom Delimiters**: You can create visually distinct delimiters:
   
   ```ruby
   puts "="*50
   puts "DEBUG START"
   puts "="*50
   ```
2. **Colorize Output**: Using the colorize gem, you can add color to your debug messages to make them pop out:
   
   ```ruby
   require 'colorize'
   puts "Debugging...".red
   ```

3. **Time-Stamped Logs**: Add timestamps to your logs to know when each message was printed:

   ```ruby
   puts "#{Time.now} - #{@user.name}"
   ```

4. **Use Vertical Space**: Insert multiple newline characters to create a visual break:

   ```ruby
   puts "\n\n\n"
   puts @user.inspect
   puts "\n\n\n"
   ```

5. **Hierarchy Indicators**: If you're debugging nested loops or recursive functions, you can create a visual hierarchy:

   ```ruby
   puts "--- Level 1 ---"
   puts "------ Level 2 ------"
   ```

6. **Custom Debugging Method**: Create a custom debug printing method to automate some of the patterns you frequently use:

   ```ruby
   def custom_debug(message, delimiter="*")
     puts delimiter * 30
     puts message
     puts delimiter * 30
   end
   ```

7. **Tabulate Data**: If you're printing arrays or collections, presenting them in a tabulated format can be more readable:

   ```ruby
   @users.each do |user|
     puts "| #{user.id} | #{user.name} | #{user.email} |"
   end
   ```

8. **External Libraries for Formatting**: Use libraries like awesome_print to get well-formatted and colorized output:

   ```ruby
   require 'awesome_print'
   ap @user
   ```

9. ActiveRecord Queries: Print the actual SQL query being executed by an ActiveRecord query:

   ```ruby
   puts User.where(email: 'test@email.com').to_sql
   ```

10. **ActiveModel Attributes**: Instead of printing the whole object, just print the attributes:
    ```ruby
    puts @user.attributes.to_s
    ```

11. **Dump Object to a File**: If the object is too large, dump it into a file to inspect later:

    ```ruby
    File.open("debug_output.txt", "w") { |f| f.write(Order.all.inspect) }
    ```
