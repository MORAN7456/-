<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Вход и Регистрация</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 400px;
            margin: auto;
            background: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            text-align: center;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
        }
        input[type="text"],
        input[type="email"],
        input[type="password"] {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        input[type="submit"] {
            background: #5cb85c;
            color: #fff;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
        }
        input[type="submit"]:hover {
            background: #4cae4c;
        }
        .message {
            text-align: center;
            margin: 10px 0;
            color: red;
        }
        .welcome {
            text-align: center;
            margin: 20px 0;
            color: green;
            font-weight: bold;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Вход</h2>
    <?php
    $welcomeMessage = "";

    // Обработка формы входа
    if ($_SERVER['REQUEST_METHOD'] === 'POST') {
        if (isset($_POST['action']) && $_POST['action'] === 'login') {
            $username = $_POST['username'];
            $password = $_POST['password'];

            // Здесь можно добавить код для проверки пользователя в базе данных
            // Пример: if (check_user($username, $password)) { ... }

            // Для примера, предположим, что вход успешен
            $welcomeMessage = "Добро пожаловать, $username!";
        }

        if (isset($_POST['action']) && $_POST['action'] === 'register') {
            $username = $_POST['username'];
            $email = $_POST['email'];
            $password = $_POST['password'];

            // Здесь можно добавить код для сохранения пользователя в базе данных
            // Пример: if (register_user($username, $email, $password)) { ... }

            // Для примера, предположим, что регистрация успешна
            $welcomeMessage = "Добро пожаловать, $username!";
        }
    }
    ?>
    <form action="" method="POST">
        <input type="hidden" name="action" value="login">
        <div class="form-group">
            <label for="login-username">Имя пользователя</label>
            <input type="text" id="login-username" name="username" required>
        </div>
        <div class="form-group">
            <label for="login-password">Пароль</label>
            <input type="password" id="login-password" name="password" required>
        </div>
        <input type="submit" value="Вход">
    </form>
    <?php if ($welcomeMessage): ?>
        <p class="welcome"><?php echo $welcomeMessage; ?></p>
    <?php endif; ?>
</div>

<div class="container" style="margin-top: 20px;">
    <h2>Регистрация</h2>
    <form action="" method="POST">
        <input type="hidden" name="action" value="register">
        <div class="form-group">
            <label for="register-username">Имя пользователя</label>
            <input type="text" id="register-username" name="username" required>
        </div>
        <div class="form-group">
            <label for="register-email">Электронная почта</label>
            <input type="email" id="register-email" name="email" required>
        </div>
        <div class="form-group">
            <label for="register-password">Пароль</label>
            <input type="password" id="register-password" name="password" required>
        </div>
        <input type="submit" value="Регистрация">
    </form>
    <?php if ($welcomeMessage && !isset($_POST['action'])): ?>
        <p class="welcome"><?php echo $welcomeMessage; ?></p>
    <?php endif; ?>
</div>

</body>
</html>
