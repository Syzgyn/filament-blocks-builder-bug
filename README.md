# To Reproduce
```
git clone https://github.com/Syzgyn/filament-blocks-builder-bug.git
cd filament-blocks-builder-bug
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
```

`php artisan make:filament-user`

`php artisan serve`

- Go to the admin panel at `http://127.0.0.1:8000/admin` and login
- Click 'Contents' on the left, then create a new content
- It doesn't matter what content you add, as soon as you save it will fail

# Presumed Cause
`https://github.com/laravel/framework/blob/11.x/src/Illuminate/Database/Query/Grammars/Grammar.php#L1171`

The `$values` being passed to `compileInsert` for a normal model is an array of strings, ints, etc.  The check on the above line then normally wraps everything in another array.  

In this case though, the block content is the first element of the array, preventing the pending model content from being wrapped in another array, and causing the type error.