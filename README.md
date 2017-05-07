Roundcube-AutoLogin
===================

This class allows you to automatically login to RoundCube

# Important

For this class to work, the RoundCube installation has to be on the same domain the code is run. Because you can not set cookies on another domain. It also needs cURL to function correctly.

# Usage

Usage is very simple, you only need RoundcubeAutoLogin.php, cookiejar.txt is created and deleted on the fly.
(you can rename it, but you have to rename it in the code as well). 

1. Using from a php schript:
Just include the class and the following code in your php script:

```
    // set your roundcube domain path
    $rc = new RoundcubeAutoLogin('http://domain.com/roundcube/');
    $cookies = $rc->login('email', 'password');
    // now you can set the cookies with setcookie php function, or using any     other function of a framework you are using
    foreach($cookies as $cookie_name => $cookie_value)
    {
        setcookie($cookie_name, $cookie_value, 0, '/', '');
    }
    // and redirect to roundcube with the set cookies
    $rc->redirect();
```

2. Using script as is:
Just place the RoundcubeAutoLogin.php on your webserver, e.g. in the roundcube diretory,
include this form in you HMTL code and let it point to where you placed the script.

```
    <form action="http://domain.com/roundcube/RoundcubeAutoLogin.php" method="post" name="autologin">
        UserID <input name="rc_user" type="text" id="rc_user">
        Passwort <input name="rc_pass" type="password" id="rc_pass">
        <input type="submit" name="Submit" value="login">
    </form>
```
In both cases you should be automatically redirected to your Roundcube installation and you should be logged in.

# Contributing

This class is brand new, so if you have any improvements please submit a pull request. For instance debugging should become easier etcetera.
