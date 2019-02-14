# probleme-migration-with-laravel error 42000 or 42501 or 42.....
When you have some error with the php artisan migrate like : 

- "In Connection.php line 664:
SQLSTATE[42S01]: Base table or view already exists: 1050 Table 'users' alre  
ady exists (SQL: create table `users` (`id` int unsigned not null auto_incr  
ement primary key, `name` varchar(255) not null, `email` varchar(255) not n  
ull, `password` varchar(255) not null, `remember_token` varchar(100) null,   
`created_at` timestamp null, `updated_at` timestamp null) default character  
 set utf8mb4 collate utf8mb4_unicode_ci)"                                                                                                                 
or
- "In Connection.php line 458:                                                                          
SQLSTATE[42S01]: Base table or view already exists: 1050 Table 'users' alre  
ady exists"
or
- "Illuminate\Database\QueryException  : SQLSTATE[42000]: Syntax error or access violation: 1071 Specified 
key was too long; max key length is 767 bytes (SQL: alter table `users` add unique `users_email_unique`(`email`))"
or
- "PDOException::("SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long; max key length is 767 bytes")"

<h2>For resolve it : </h2>
 
 <h4>edit your AppServiceProvider.php file and inside the boot method set a default string length:</h4>
 
  - 1 : add this path --> use Illuminate\Support\Facades\Schema;
  
  - 1 Bis : Add this
  " public function boot()
   {
    Schema::defaultStringLength(191);
   }                                   "

  - 2 : make the command : "php artisan migrate:fresh"
  
  - 3 : All is fine !
