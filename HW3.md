# HW3

## General
- Please give us more informative READMEs... In particular I want to know how to setup. If you give us a SQL file, tell us what are we supposed to do with it. Give us commands to be executed in our terminals!
- Pay attention to code style, such as indentation, spaces, etc. There are lots of code formatters/linters online; Google them!
- DRY (Don't Repeat Yourself): try to write the same piece of code at most twice. Here is an example:

    ```php
    echo "<th>ID</th>";
    echo "<th>Task</th>";
    echo "<th>Done?</th>";
    echo "<th>Deadline</th>";
    echo "<th>Tags</th>";
    ```

  Imagine if you want to add another row some time in the future. You will need to manually add them in every table you created! It's much better to do something like:

  ```php
  $rows = ['ID', 'Task', 'Done?', 'Deadline', 'Tags'];
  foreach ($arr as $val) {
      echo "<th>$val</th>";
  }
  ```

Much cleaner. You can just edit the `$rows` variable if you want to add other rows.
- Don't store password unencrypted in database! If your database is compromised, hackers will be able to gain access easily. Check out http://php.net/manual/en/faq.passwords.php
- Please don't ever use:
  - double equals `==`.
  - `die();`. Throw an exception instead.
- For config files, generally the solution is to:
  - add `config.php` to `.gitignore`
  - create a `config.php.default` file that contains `config.php` without sensitive information such as passwords
  Then, when users want to clone and set up your project, they can just copy `config.php.default` to `config.php` and fill in according to what they need. Cool right? You might think "it's only for development anyways", but remember that your project can be used in production as well! You certainly won't want your production credentials to be checked out to Github.

## emer7/To-do_list
- Much better to have a header.php file and have the files include from that file. If you only include bootstrap, imagine if you need to include another CSS file; you need to include it in every file.
- This comment: `// If result matched $myusername and $mypassword, table row must be 1 row` I don't really like it. What if two users have the same username? I think it suits better to have `$count > 0` instead.

## Alina-PANG/HW3
- In backend/login.php you only need `session_start();` once.
- In backend/new_post.php: `if ($conn->query($sql) === TRUE)` can be simplified to `if ($conn->query($sql))`.
- This code:

    ```php
    for($i=0;$i<3;$i++){
        echo "<br>";
    }
    ```

  Consecutive `<br>` tags are always bad. Use CSS instead.
- In your views/personal_index.php don't mix php logic in! Try to create a function that encapsulates the logic and use it in your views. For example,

    ```php
    <div id="conbody">
    <?php
        $name = $_SESSION['username'];
        $sql = "SELECT * FROM tbl_posts WHERE user_name='$name'";
        $result = $conn->query($sql);
        if ($result->num_rows > 0) {
            while($row = $result->fetch_assoc()) {
                echo "Title: " . $row["title"]."<br><br>";
                //$cont = wordwrap((string)$row["content"], 60, "\n", false);
                echo $row["content"]."<br><br>";
                //echo chunk_split($row["content"], 60);
                echo "created on " . $row["update_time"]. $row["update_date"] . "<br>";
                for($i=0; $i<3;$i++){ echo "<br>";}
            }
        }
        else {
            echo "Empty String";
        }
        $conn->close();
    ?>
    </div>
    ```

  Put this in a function and change it to something like:

  ```php
      <div id="conbody">
      <?php content_data($username) ?>
      </div>
  ```

  Much cleaner right? I can now see clearly what goes inside the div.

## HanamaruSS/to-do-list
- Abstract the tags inside head.
- This code:

    ```php
    if ($order === "" || ($order !== "task" && $order !== "deadline" && $order !== "done" && $order !== "admin")) {
        $order = "deadline";
    }
    if ($order === "admin") {
        $order = "admin_id";
    }
    ```

  Better would be something like:

  ```php
  $allowed_order = ["task", "deadline", "done", "admin"]
  if ($order === "admin") {
      $order = "admin_id";
  } else if !(in_array($order, $allowed_order)) {
      $order = "deadline"
  }
  ```

- This code:

    ```php
    echo "<th><a href='/?o=task'>Task</a></th>";
    echo "<th><a href='/?o=deadline'>Deadline</a></th>";
    echo "<th><a href='/?o=done'>Is it done?</a></th>";
    echo "<th>Tag(s)</th>";
    echo "<th><a href='/?o=admin'>Created by<th></tr></thead>";
    ```

  can be simplified to something like:

  ```php
  $headers = ["Task" => "task", "Deadline" => "deadline", "Is it done?" => "done", "Tag(s)" => NULL, "Created by" => "admin"];
  foreach ($array as $key => $value) {
      if ($value === NULL) {
          echo "<th>$key</th>";
      } else {
          echo "<th><a href='/?o=$value'>$key</a></th>";
      }
  }
  ```

- Usually junction tables (I call them join tables) are named according to the two tables it joins. In this case it is better to call it todo_tag, for example.

## KhooDesmond/Blog

Waiting :3
