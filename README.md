# To Reproduce
```
git clone https://github.com/Syzgyn/filament-blocks-builder-bug.git
cd filament-blocks-builder-bug
composer install
php artisan migrate
```

`php artisan make:filament-user`

`php artisan serve`

- Go to the admin panel at `http://127.0.0.1:8000/admin` and login
- Click 'Contents' on the left, then create a new content
- It doesn't matter what content you add, as soon as you save it will fail