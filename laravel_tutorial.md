# Laraval tutoraial Notes
    https://www.youtube.com/watch?v=dJo7zVycSF8&list=PL8p2I9GklV44dF7G_uPK_9ZHCQon15flp&index=2

# Tools for laravel
 - Mysql and php or xampp
 - Php latest version or PHP 8
 - Composer

# Laravel Prerequisites
 - Enviroment
 - Basic PHP and Database
  - OOPs

#  How to go with laravel 
  - insatall basic tools
  - Understand laravel file structure
  - learn basics and do spractice

# What is MVC
  - MVC(Model-View-Controller)
  - MVC is a pattern in software design commenly used to
      implement user interfaces, data, and controlling login.
  - Model: Manages data and business logic
      View: Handles layout and display
      controller: Routes commands to to model and view

# Composer
  - A dependency manager for php.
   Install-package with dingle command
   Can update version package, framework etc.
   Composer can be used with any frameworks
   Similar like NPM in Node

   ## Steps
   - Install Composer(Once)
   - Install Laravel (Once)
   - Make Project
   - Run Project :)
  
   ### Then see the and apply in given xampp driver using cmd
    https://getcomposer.org/download/
   
   - composer  // to see the all list
   - composer --version  // see the version

#   
    --> composer global require "laravel/installer=~1.1"   // globally install the laravel in cmd
    -->  C:\Users\manish\AppData\Roaming\Composer\vendor\bin   // set the path 
    --> create in given folder create "laravel new blog9"
    --> composer global remove laravel/installer
    --> composer global require laravel/installer
 
#
    --> cd floldername //like cd blog9
    --> to start server //php artisan serve

    php artisan serve

# Folder Structure
  ### where we write
    - Html
    - Model
    - Controller
    - Routing
    - File store
    - Config
    - Dependency file
#
-  Https --> controlers // is centeral unit controls ### which handles model and view
   - Middleware ---> 1.user access webite 2. filter - user
   - kernal.php -->  middleware register to use
   - Models/users.php ----> user name database table 
   
### which we connected
    - provider ----> Service provider
    - boostrap: laraval file itegrate with - html.             
    - cache 
    - config --->configration
                app.php, auth.php, database.php
    - database ---> dummy work , table data schema work
    - public---> assets,allcss
                index.php --> first file load in laraval project
                .htaccesss --> change some configration
    - resources --> views --> all html to work
    -  routes --->
        - api.php
        - channels.php
        - console.php
        - web.php
        - tests folder ---> we do test case
 
# Create the first File
        ---> Make First Change in File
        ---> Create First File
        ---> Intreview Question

# create file in views --->todo.php
        setup in routes ---> web.php

# Routing
        ---> What is Routing
        ---> How to make Routing
        ---> Pass data with Routing
        ---> Anchor Tag
        ---> Redirect
   #
    Note:- 
    -url 
    -page
   #
    1. 
    - Large Way
        Route::get('/about', function () {
        return view('about');
        });
    - Small Way
        // small way to write
        Route::view("about" , '/about');

  #

    2. 
    Pages was pass the data dynamic page
       ---> for this we have to set parameter

       http://localhost:8000/manish

      1.  
         Route::get('/{name}', function ($name) {
           echo $name;
           return view('welcome');
         });
       
      2. Give 
         
         routes 
         ---> web.php
               Route::get('/{name}', function ($name) {
                  return view('welcome', ['name'=>$name]);
                });
         views
         ---> welcome.blade.php
              data pass dynamic <h1>{{$name}}</h1>
         
       3. anchor tag
        <nav>
          <li><a href="/">Home</a></li>
          <li><a href="/about">About</a></li>
          <li><a href="/contact">Contact</a></li>
        </nav>

       4. Redirect tag
          Redirect home page to about page
          Route::get('/', function () {
             return redirect('about');
          });
       5. web.php => api.php what is this (interview ques)
    

  
#  Controller
    --> what is Controller
    --> Make Controller
    --> Make Function in Controller
    --> Call Controller from Routing
    --> Pass Params with URL
      
    1. make controller --->app/Http/Controller
       
       1.In cmd create
       php artisan make:controller UserController

       2.in UserController write the function

       3. routes
           ----> web.php
               ---> Route::get('user', [UserController::class,'show']);
               ----->show is function which is in controller
               ------>UserController is in controller
       4. 
          1. from these we can connect with database
          2. from these we can call views
          3. also called centeral unit
 
# Laravel Component //imp
    ---> what is component
    ---> Make Component
    ---> Use Component
    ---> Pass Data in Component

    1. php artisan make:component Header 
       --->Two place it changes 
           -->1. resources 
                    -->views
                        --->components
                              --> header.blade.php // Html file

            
            -->2. app
                   ---> View
                        ---> Header.php    
    2. Use components
         1. point from up we see th resource --> viewa --> components --> header
            to call in page we write <x-header /> or you say <x-component file name />
            which we use more and more.
         2. <x-header componentName ="Users" /> Users is that file name which is call.
             go to up 2. point app --> view --> header.php
         3. if you use the user component name
              <x-header componentName="Users" /> // users.blade.php == componentName 
             put in app-- view -- header.php

    
  # Laravel view  //resources ---> views
       ---> What is View
       ---> Make Make
       ---> Call View
       ---> Pass Data in View
   # Laravel Blade Template
       ---> what is Blade Template
       ---> Blade Template Expression
       ---> Conditions      //imp
       ---> For and Foreach Loop //imp
      
       blade template to give
       1. create controller in cmd or app/http/controllers/controller name
       2. create template in resources/views/users.blade.php
       3. connect template users.blade.php and controllers  in routes/web.php 
       4.<h2>Hello, {{$users}}</h2> in template
       5. in controller give the array values
          <h2>{{count($names)}}</h2>
       6. in template
            @if($names=="anil")
            <h2>Hii , {{$names}}</h2>
            @elseif($names=="sam")
            <h2>Hii , {{$names}}</h2>
            @else
            <h2>Hi ,unknown</h2>
            @endif
          in controllers
              function loadView()
              {
                //   return view("users");
               //  return view("users" , ["users"=>'anil']);
              // return view("users" , ["names"=>['anil' , 'bruce' , 'silpa']]);
                return view("users" , ["names"=>'sam']);
              }
       7. for work
           @for($i=0;$i<10;$i++)
           <h4>{{$i}}</h4>
           @endfor
       8.
          In template
          @foreach ($names as $name)
             <h6>{{$name}}</h6>
           @endforeach
       
       9. In controller loadview
 
        $data=['anil' , 'sam' , 'tonny'];
        return view("users" , ["names"=>$data]);
# Laravel Blade Part2
     --> Include View in View
     --> Php in Js
     --> Csrf token
     --> Header and Footer
     1. call of differnt blade file @include('innerusers')
     2. @csrf
     <script>
         var data = @json($names);
         console.log(data);
     </script>
# Laravel Html Form
    --> Make Html Form
    --> Make Controller
    --> Route Get and post 
    --> Get Form Data
    1. first make the form subission form
       when submit it will give 419 error
       to avoid these error use @csrf
    2. How to pass data
       Route::view("innerusers" , '/innerusers');
       Route::view("form" , '/form');
       // Route::get("url", "file"); 
       Route::post('form', [InnerUserController::class, 'formView']);
       Route::view('login', 'form');
    3. Get the value work in controller class
        function formView(Request $req)
        {
        return $req->input();
        } 
        <h1>My data</h1>
       <form action="form" method="POSt">
         @csrf
       <div>
           <input type="text" name="username" placeholder="Enter the Username" id="" />
       </div>
        <div>
           <input type="password" name="password" placeholder="Enter the password" >
        </div>
        <div>
           <button type="submin">Login</button>
        </div>
       </form>
 
# Laravel Form Validation
    --> Use Validation function
    --> Show error message
    ---> Error with every field

    1. form.blade.php
       -->
          {{$errors}}
       -->
         @if ($errors->any())
           @foreach ($errors->all() as $err)
              <li>{{$err}}</li>
           @endforeach
         @endif
     2. error will show up
        <h1>My data</h1>
        @if ($errors->any())
            @foreach ($errors->all() as $err)
             <li>{{$err}}</li>
            @endforeach
        @endif
       <form action="form" method="POSt">
          @csrf
        <div>
          <input type="text" name="username" placeholder="Enter the Username" id="" />
        </div>
        <div>
         <input type="password" name="password" placeholder="Enter the password" >
        </div>
        <div>
        <button type="submin">Login</button>
        </div>
       </form>
    3. More and more validation use
        
       function formView(Request $req)
       {
           $req->validate([
              'username'=>'required',
              'password'=>'required'
           ]);

          return $req->input();
        }
    4. 
     <h1>My data</h1>
       <form action="form" method="POSt">
          @csrf
         <div>
            <input type="text" name="username" placeholder="Enter the Username" id="" />
            <span>@error('username'){{$message}} @enderror</span>
        </div>
        <div>
            <input type="password" name="password" placeholder="Enter the password" />
            <span>@error('password'){{$message}} @enderror</span>
        </div>
         <div>
            <button type="submin">Login</button>
         </div>
       </form>

# Laravel Middleware
     
    -->What is Middleware
    -->Middleware Type
    -->Make Middleware
    -->Apply Middleware

     1. to make Middleware
        php artisan make:middleware checkAge
        -->in checkAge middleware the write
          public function handle(Request $request, Closure $next): Response
          {
             return $next($request);
             if($request->age && $request->age<18)
             {
                return redirect('no access');
             }
          }
        --->in web.php
            Route::view("noacess" , '/wmiddleware');
        ---> in views --> middleware.blade.ph
             --><h1>Do not get access</h1>
        ---> middleware created but not apply 
             --> app/Http/Kernal.php

        ---> protected $middleware = [
        \App\Http\Middleware\checkAge::class,
    
        --->see the middeware work  redirect in noaccess
        http://localhost:8000/?age=10

        --> How to see middleware global
# Laravel Group Middleware
      --> What is group Middleware
      --> Make Middleware
      --> Register it 
      --> Apply Middleware
 # Laravel Route Middleware
      --> What is Route Middleware
      --> Make Middleware
      --> Register it
      --> Apply Middleware
  
# Laravel Start with DB
      -->Config database
      -->Checkout Database
      -->Import DB class
      -->Fetch Data from mysql

     -->  Go to env
          --> DB_DATABASE=blog  into DB_DATABASE=
             DB_USERNAME=root   into DB_USERNAME=
             DB_PASSWORD=       into DB_PASSWORD=
     ---> Go config /database.php see env("") code
   ###  How to create the phpmyadmin xampp database
      1. Start xampp active localhost and mysql
      2. create database: blog in phpmyadmin
      3. create collection: users 
      4. create table and insert value

     output: you get value in json format
     class UserDatabaseController extends Controller
     {
    //
         function index()
         {
           // echo DB::select("select * from users") ;
           return DB::select("select * from users") ;
        }
    }


# Laravel Model with DB
    1. What is model
    2. Make Model
    3. Fetch Data from Model
    4. Show Data

    --> Map Database table with calss name
    --> Define database structure
    --> Write Business Login

    lets's say database collection table name is : users i create the model user 
    it map automatically
    
    models name singuler --> user
    collection table plural -->users

    database table: emp = modeles name is emp 
    So its possible to write one line

    --> To create the model
        php artisan make:model User
        taking 'User' model name because be database table name: users
       
        how to use model  
        Without controler you cannot go directly to route
        1. import model in controller 
           write function in UserController
           class MuserdbaseController extends Controller
           {
                //All data show 
               function getData()
               {
                     return User::all();
                 }
            }
        2. the go to routes
           create new table in same database
           get new employee data
           class User extends Model
           {
              use HasFactory;
              public $table="employee";
           }
# Laravel Http Client
    
    What is Http Client
    How to use Http Client
    Send Data to View
    Show Data in HTML Table
    
    ---> Get api call help from Http Client
    1. make controls to route 
        //Https work
        Route::get("htpusers" , [HtpClientController::class, 'index'] );
    2. in controller write function
        class HtpClientController extends Controller
        {
            //
            function index(){
            // echo "apicall be here";

            return Http::get("https://dummyjson.com/users"); //api calls
            }
        }
    3. How to view or render in html
        //Https work in api route
        Route::get("apifetch" , [HtpClientController::class, 'index'] );
        // Https control route
        class HtpClientController extends Controller
            {
            //
                function index(){
                // echo "apicall be here";
                // return Http::get("https://dummyjson.com/users");
                $data =  Http::get("https://dummyjson.com/users");
                return view('apifetch' , ['collection'=>$data['users']]);
                }
            }
        //htlm apifetch.blade.html
        <h1>User list</h1>

        <table border="1">
            <tr>
            <th>Id</th>
            <th>Name</th>
            <th>email</th>
            <th>Profile Photo</th>
            </tr>
    
            @foreach ($collection as $item)
            <tr>
            <td>{{$item['id']}}</td>
            <td>{{$item['firstName']}}</td>
            <td>{{$item['email']}}</td>
            <td><img src={{$item['image']}} alt=""></td>
            </tr>
            @endforeach


            </table>

# Laravel Http Request Method /post/put/patch
    ---> What is Http Request
    ---> Http Request Method
    ---> Make Html Form
    ---> Route Method For Request

    List of Http
    GET
    POST
    PUT
    HEAD
    DELETE
    PATCH
    OPTIONS
  ### simple get Method 
    1. Create Controllers
        class HptreqController extends Controller
        {
            //
            function testReq(Request $req){
            // echo "form submitted";
            // echo $req->input();
            return $req->input();
            }
        }

    2. create route in web.php
        //Https Requests
        Route::get("hreq" , [HptreqController::class , 'testReq']);
        Route::view("login" , "hreq");

    3. in view hreq.blade.php
        <h1>User Login</h1>

        <form action="hreq" method="GET">
            @csrf
            <div><input type="text" name="username" id=""></div>
            <div><input type="password" name="password" id=""></div>
            <div><button>Login</button></div>
        </form>
    4. how to create PUT
        //Https Requests in web.php

     Route::put("hreq" , [HptreqController::class , 'testReq']);
     Route::view("login" , "hreq");

     //hreq.blade.php
     <h1>User Login</h1>

     <form action="hreq" method="POST">
       @csrf
       {{method_field('PUT')}}
       <div><input type="text" name="username" id=""></div>
       <div><input type="password" name="password" id=""></div>
       <div><button>Login</button></div>
     </form>
# Laravel Flash Session
    ---> What is Flash Session
    ---> Store data in Flash Session
    ---> Get data from Flash Session
    ---> Delete data from Session

    1. Normal Session can use repaeat but flash session cannnot be repeat
    2. Uses data save when we redirected diffrent page we have give message like
        data has been save , email have been send.
    3. for code we need view and controller and all of these we need routes.
    
    --->storeuser.blade.php

    <style>
    div{
        padding-bottom: 10px;
    }
    </style>


    <h1>Add New Member</h1>

    @if(session('username'))
        <h3>Data saved for {{session('username')}}</h3>
    @endif
    <form action="storecntrl" method="POSt">
        @csrf
        <div>
            <input type="text" name="username" placeholder="Enter the name">
        </div>
        <div>
            <input type="password" name="password"   placeholder="Enter the password">
        </div>
        <div>
            <input type="email" name="email" placeholder="Enter user email">
        </div>
        <button type="submit">Add User</button>
        </form>

   ---> FstoreController.php

     class FstoreController extends Controller
    {
    //
    function store(Request $req)
    {
        // return $req->input();
        // we heve to store the username 
        $data =  $req->input('username');
        $req->session()->flash('username' , $data);
        // return view('') // for same page
        return redirect('store');
     }
    }

    ---> web.php
        // flash season

        Route::view('store' , 'storeuser');
        Route::post('storecntrl' , [FstoreController::class , 'store'] );

# Laravel Session
    ---> Make  Login Form
    ---> Store data in session
    ---> Get data from Session
    ---> Delete data from Session

    --->loginess.blade.php

        <style>
        div{
            padding-bottom: 10px;
            }
        </style>
 
 
    <h1>User Session Login</h1>
    
    <form action="/usersesslogin" method="POST">
        @csrf
        <div>
            <input type="text" name="username" placeholder="Enter the name">
        </div>
        <div>
            <input type="password" name="password"   placeholder="Enter the password">
        </div>
        <button type="submit">Add User</button>
    </form> 

    ----> web.php

  // session
 
     // Route::view('login' , 'loginses');
     Route::view('profile' , 'profile');
     Route::get('/logoutses' , function() {
       if(session()->has('username'))
       {
        session()->pull('username', null);
       }
        return redirect('login');
      }); 
      Route::get('/login' , function() {
    if(session()->has('username'))
    {
        return redirect('profile');
    }
     return view('loginses');
    });
    Route::post("usersesslogin" ,[SloginController::class, 'userworkLogin']);

    ---> SloginController.php

    class SloginController extends Controller
    {
        //
        function userworkLogin(Request $req)
        {
        //    return  $req->input();
        $data = $req->input('username');
        $req->session()->put('username', $data);
        // echo session('username');
        return redirect('profile');
        }

    }

    ---> profile.blade.php

    <h1>Profile Page</h1>
    <h2>Hello , {{session('username')}}</h2>
    <a href="/logoutses">Logout</a>

# Upload file in laravel
        --> Make View
        --> Make Html Form
        --> Make Controller
        --> Code for upload file

    1. Making upload.blade.php
        <h1>Upload File</h1>
            <form action="upload" method="POST">
            @csrf
            <input type="file"  name="file">
            <button type="submit">Upload file</button>
            </form>
    2. Route::view('upload' , 'upload');

# Laravel Localization
    1. What is Localization
    2. How to Define Localization
    3. Set Default Locale
    4. Set Locale with Route
   
    notes:
    1. change the localization translate language eng into chinese , japanese, korian , hindi

# User List From DB
    1. Make Model
    2. make Controller and view
    3. Fetch Data from db table
    4. show data on html page

    to start the srver //php artisan serve

    ---> start of list 
    --> make the database give env
    --> In database make table name Members
    --> Give fiels id (auto increment) , name , email ,address
    --> make the Members.php Model
    --> Make controlers MembersController.php
        <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Members;


        class MembercONTROLLER extends Controller
       {
        //
        function show(){
            // return "hello form Membercontroller";
            // return view('list');
            // return Members::all();
            $data= Members::all();
            return view('list', ['members'=>$data]);
        }
        }

    ---> make web.php 
        Route::get('list', [MembercONTROLLER::class, 'show']);
    ---> Views make template list.blade.php
        <h1>Member List</h1>
        <table border="2">
        <tr>
            <th>Name</th>
            <th>Email</th>
            <th>Address</th>
        </tr>
        @foreach ($members as $memlist)
        <tr>
            <td>{{$memlist['name']}}</td>
            <td>{{$memlist['email']}}</td>
            <td>{{$memlist['address']}}</td>
        </tr>
        @endforeach
        </table>
  
# Laravel Paginatin

      1. Make Model
      2. Make Controller and View
      3. Fetch Data from DB table
      4. Show Data with Pagination

    -----> Only use MembercONTROLLER.php
        <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Members;


    class MembercONTROLLER extends Controller
    {
        //
        function show(){
            // return "hello form Membercontroller";
            // return view('list');
            // return Members::all();
            $data= Members::paginate(5);  //limits set
            return view('list', ['members'=>$data]);
        }
    }

    -------------> list.blade.php

    <h1>Member List</h1>
        <table border="2">
        <tr>
            <th>Name</th>
            <th>Email</th>
            <th>Address</th>
            </tr>
            @foreach ($members as $memlist)
            <tr>
            <td>{{$memlist['name']}}</td>
            <td>{{$memlist['email']}}</td>
            <td>{{$memlist['address']}}</td>
            </tr>
            @endforeach
        </table>

        <div>
            {{$members->links()}} // for pagination links
        </div>


# Save Data in Database
    - Make Html From in View
    - Make Controller and Model
    - Make Route
    - Save Data in Table

    1. make the  addmember.blade.php

    <h1>Add Members</h1>
    <form action="" method="POST">
        @csrf
        <div>
            <input type="text" name="name" placeholder="Enter Name" >
        </div>
        <div>
            <input type="email" name="email" placeholder="Entre Email">
        </div>
        <div>
            <input type="text" name="address" placeholder="Enter The address">
        </div>
        <button type="submit">Add Member =</button>
    </form>
    2. make controller MemberDataControler.php
        <?php

        namespace App\Http\Controllers;

        use Illuminate\Http\Request;
        use App\Models\Members;

        class MemberDataController extends Controller
        {
        //
            function addData(request $req)
        {
        $member = new Members; 
        $member->name=$req->name;
        $member->email=$req->email;
        $member->address=$req->address;
        $member->save();
        return redirect('add');
        }
        }
    3. make model as a database table name like 
        Models
        --> members.php
            <?php

            namespace App\Models;

            use Illuminate\Database\Eloquent\Factories\HasFactory;
            use Illuminate\Database\Eloquent\Model;

            class Members extends Model
            {
                use HasFactory;
                public $timestamps=false;
            }
    4.  Give the route in web.php
        Route::post('add',[MemberDataController::class, 'addData']);
        Route::view('add','addmember');

# Delete Data in Database
    --> Make Model and Controller
    --> List with Delete Button
    --> Make Route
    --> Delete Data in Table

    1. Make the Controller
     <?php

      namespace App\Http\Controllers;

      use Illuminate\Http\Request;
      use App\Models\Members;

      class MemberDataController extends Controller
      {
         //
          function listData(){
            // return view('deletedatalist' );
            $data= Members::all();
            return view('deletedatalist', ['members'=>$data]);
         }
          function deleteData($id){
            $data = Members::find($id);
            $data->delete();
            return redirect('listData');
         }
      }

    2. Take models make members.php 
        <?php

        namespace App\Models;

        use Illuminate\Database\Eloquent\Factories\HasFactory;
        use Illuminate\Database\Eloquent\Model;

        class Members extends Model
        {
            use HasFactory;
            public $timestamps=false;
        }

    3.  Make MemberDataController.php
        <?php

        namespace App\Http\Controllers;

        use Illuminate\Http\Request;
        use App\Models\Members;

        class MemberDataController extends Controller
        {
        //
            function listData(){
            // return view('deletedatalist' );
            $data= Members::all();
            return view('deletedatalist', ['members'=>$data]);
            }
        function deleteData($id){
            $data = Members::find($id);
            $data->delete();
            return redirect('listData');
            }
        }
    4. deletedatalist.blade.php
    <h1>Delete data from list</h1>
    <table border="1">
    <tr>
        <th>Name</th>
        <th>Email</th>
        <th>Address</th>
        <th><Button>All Delete</Button></th>
    @foreach ($members as $item)
    <tr>
        <td>{{$item['name']}}</td>
        <td>{{$item['email']}}</td>
        <td>{{$item['address']}}</td>
        <td><a href={{"delete/".$item['id']}}>Delete</a></td>
    </tr>
    @endforeach
    </table>

    5. In web.php

    Route::get('listData',[MemberDataController::class, 'listData']);
    Route::get('delete/{id}',[MemberDataController::class, 'deleteData']);

# Update Data in Database
    --> Make Model and Controller
    --> List with Edit Button
    --> Make Route
    --> Edit Data in Table

    1. Create a listdata where you see the deletedatalist.blade.php
    <h1>Delete data from list</h1>
    <table border="1">
    <tr>
        <th>Name</th>
        <th>Email</th>
        <th>Address</th>
        <th><Button>All Delete</Button></th>
    @foreach ($members as $item)
    <tr>
        <td>{{$item['name']}}</td>
        <td>{{$item['email']}}</td>
        <td>{{$item['address']}}</td>
        <td><a href={{"delete/".$item['id']}}>Delete</a>
        <a href={{"edit/".$item['id']}}>Edit</a></td>
    </tr>
    @endforeach
    </table>

    2. create controller MemberDataContoller

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Members;

    class MemberDataController extends Controller
    {
        //
        function listData(){
            // return view('deletedatalist' );
            $data= Members::all();
            return view('deletedatalist', ['members'=>$data]);
        }
        function deleteData($id){
            $data = Members::find($id);
            $data->delete();
            return redirect('listData');
        }
        function showData($id){
            // return Members::find($id);
            $data=Members::find($id);
            return view('edit', ['data'=> $data]);
        }
        function update(Request $req)
        {
            $data= Members::find($req->id);
            $data->name=$req->name;
            $data->address=$req->address;
            $data->email=$req->email;
            $data->save();
            return redirect('listData');
        }
    }

    3. edit.blade.php

    <h1>Update Member</h1>
    <form action="/edit" method="POST">
        @csrf
        <input type="hidden" name="id" value={{$data['id']}}>
        <div>
            <input type="text" name="name" value="{{$data['name']}}">
        </div>
        <div>
            <input type="text" name="address" value="{{$data['address']}}" >
        </div>
        <div>
            <input type="text" name="email" value="{{$data['email']}}" >
        </div>
        <Button type="submit">Update</Button>
    
    </form>

    4. route the data web.php

    Route::get('edit/{id}',[MemberDataController::class, 'showData']);
    Route::post('edit',[MemberDataController::class, 'update']);

    27.
    Query Builder in laravel
        --> Get Result with Table Name
        --> Where Condition
        --> Find ,Count
        --> Insert, Update, Delete

    1. Make web.php

    Route::get("listwork" ,[Members::class,'operations']);
    
    2. Make controller work Members.php
    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use Illuminate\Support\Facades\DB;

    class Members extends Controller
    {
        function operations()
        {
            // echo "Code will be here";
            // return DB::table('members')->get();

            // $data= DB::table('members')->get();
            // return view('listwork' , ['data'=>$data]);

            // return DB::table('members')
            // ->where('name' , 'tutu' )
            // ->get();
            
            // return(array) DB::table('members')->find(4);

            // return DB::table('members')->count();

            // return DB::table('members')
            // ->insert([
            //     'name'=>'anila',
            //     'email'=>'anila@lest.com',
            //     'address'=>'UKA'
            // ]);


            // return DB::table('members')
            // ->where('id', 27)->delete();

            return DB::table('members')
            ->where('id', 20)
            ->update([
            'name'=>'sila',
            'email'=>'sila@gmail.com',
            'address'=>'MK'
            ]);
        }
    }

    3. Make view listwork.blade.php

    <table border="1">
        <tr>
            <th>id</th>
            <th>Name</th>
            <th>Email</th>
        </tr>
        @foreach ($data as $item)
        <tr>
            <td>{{$item->id}}</td>
            <td>{{$item->name}}</td>
            <td>{{$item->email}}</td>
        </tr>
        @endforeach
    </table>

# Aggregates Query in laravel

    --> What is Aggregates Query
    --> Make Controller
    --> Sum,Max,Min,Avg etc
    --> Cross Check with DB

    web.php
    Route::get('crlist', [UsermemController::class, 'operation' ] );

    Make controller UsermemController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use  Illuminate\Support\Facades\DB;

    class UsermemController extends Controller
    {
        //
        function operation()
        {
        //    echo "code will rfgre be here";

        //    return  DB::table('members')->get();

        //    return  DB::table('members')->sum('id');

        //    return  DB::table('members')->avg('id');

        //   return  DB::table('members')->min('id');

        //   return  DB::table('members')->max('id');

        //    return  DB::table('members')->max('name');

            return  DB::table('members')->min('name');

        }
    }

# Join in Laravel
    --> What is Join
    --> Make Controller
    --> Import DB files
    --> Join with where condition
  

    1. make database two table employee and company give parameter
        
    2. make web.php
        Route::get('jlist', [EmployeeController::class, 'getData' ] );
    3. make controller  EmployeeController.php
        <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use Illuminate\Support\Facades\DB;

    class EmployeeController extends Controller
    {
        //
        function getData()
        {
            // return DB::table('employee')->get();
            return DB::table('employee')
            ->join('company', 'employee.id' , '=' , 'company.employee_id')
            // ->select('company.*','employee.*')
            // ->where('employee.name' , "song")
            ->where('employee.id' , 2)
            ->select('employee.name', 'company.name')
            ->get();
        }
    }

# Migration in laravel

    --> What is Migration
    --> Make Table with Migration
    --> Write code for Column Field
    --> Migrate Database

    Note:
    More then people developer use database to avoit conflict we use migration

    1. This will create file in laravel database
    php artisan make:migration create_test_table

    2. this syntax make the migrate from laravel database to localhost database
    php artisan migrate

    when some table present in localhost database then it come error

# Migration Important Command

    --> How to reset Migration
    --> Rollback Migration
    --> Rollback steps, Refresh
    --> Single file Migration

    lets's start
    
    php artisan make:migration create_test5_table
    php artisan migrate
    php artisan migrate:reset
    php artisan migrate:rollback --stop 3
    php artisan migrate --path=/database/migrations/2020_09_21_141952_create_test
    php artisan migrate:refresh


    ///////////////////////////////////////////////////////////////Revision work need ///////////////////////////////////////////

# Laravel Jetstream
    --> What is Jetstream
    --> Install jetstream
    --> Handle Database
    --> Checkout Project

    Notes:
    1. check laravel version
    2. laravel new jetblog --jet
    3. npm install
    4. npm run dev
    5. php artisan migrate
    6. php artisan  serve

    composer global remove laravel/installer
    composer global require laravel/installer

    /////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

# Laravel Accessor
    --> What is Accessor
    --> Make Controller
    --> Make Model
    --> Make a Accessor function

    Note:-
    modification in database brfore view that data

    1.Make controller

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Members;

    class MemberDataController extends Controller
    {
    
        function  listindex() {
        return Members::all();
        }
    }

    2. Make modal

    <?php

    namespace App\Models;

    use Illuminate\Database\Eloquent\Factories\HasFactory;
    use Illuminate\Database\Eloquent\Model;

    class Members extends Model
    {
        use HasFactory;
        public $timestamps=false;

        function getNameAttribute($value)
        {
            return ucfirst($value);
        }
        function getAddressAttribute($value)
        {
            return $value. ",india";
        }
    }

    3. web.php


    // Assesor

    Route::get('member' ,[MemberDataController::class, 'listindex']);


    
# Define A Mutator

    --> What is Mutator
    --> Make Controller
    --> Make Model
    --> Make a Mutator function


    Notes:-

    manually modified database

    1. 
    Create controller
    include modal name
    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Members;

    class MemberDataController extends Controller
    {

        function muterindex(){
            $membernew = new Members;
            $membernew->name="Raju";
            $membernew->email="raj123@gmail.com";
            $membernew->address="vyhgiy,lglug";
            $membernew->save();
        }
    }

    2.
    Create modal 
    <?php

    namespace App\Models;

    use Illuminate\Database\Eloquent\Factories\HasFactory;
    use Illuminate\Database\Eloquent\Model;

    class Members extends Model
    {
        use HasFactory;
        public $timestamps=false;

        // need mutator to change
        public function setNameAttribute($value)
        {
            return $this->attributes['name'] = 'Mr.' .$value;
        }
    }


    3. web.php
    include controller name
    Route::get('mumember' ,[MemberDataController::class, 'muterindex']);
  


////////////////////////////////////////////////////////////////////////////

# One to One Relation

    --> What is relations in laravel
    --> One to One Relation
    --> Make Models and controller
    --> Make relation & show

    Note:- 
    One To One
    One To Many
    One Of Many
    Many To Many
    Custom Polymorphic Types

    /////////////////////////////////////////////////////////////////////////////////

# Fluent Strings
  
    --->What is fluent Strings
    --->Issue with Privious String
    --->Userstand with Example

# Route Model Binding
 
    --> What is Route Model Binding
    --> Make Model and Controller
    --> Undersatnd with Example

    Notes
    Route and model inject
    less code to bring the databse fetch /id , /name , /etc

# First APi in laravel

    ---> MAke Controller
    ---> Make Route
    ---> Write samll code
    ---> Test ApI on postman
    ---> to start server //php artisan serve

### Note:
    In routes 
        ---> api.php

            Route::get("dataapi" , [dummyAPI::class,'getDatapi']);

        ---->make controller dummyAPI.php
            <?php

                namespace App\Http\Controllers;

                use Illuminate\Http\Request;

                class dummyAPI extends Controller
                {
                //
                function getDatapi()
                {
                    return ["id"=>1, "name"=>"Anil", "age"=>25];
                }
            }


# GET Data With API

    -->Make Controller
    -->Make Model
    -->Write Code for API
    -->Test API on Postman

    routes
    ---> api.php
    Route::get("Listdataapi" , [DeviceController::class,'listoddata']);

    Create a Controller DeviceController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Device;
    use App\Models\Members;

    class DeviceController extends Controller
    {
        //
        function listoddata()
        {
            return Device::all();
        }
    }

    create a modal Device.php
    --> In this specify timestaps and table

    namespace App\Models;

    use Illuminate\Database\Eloquent\Factories\HasFactory;
    use Illuminate\Database\Eloquent\Model;

    class Device extends Model
    {
        use HasFactory;
        public $timestamps=false;
        public $table="device";
    }

    Get value in postman

    1. Click + 
    2. GET Search http://localhost:8000/api/Listdataapi

40.

    Get API with Params
    --> Pass Params with Routing
    --> Condtion with Route
    --> Apply Condition with Result 
    --> Other Options


    ---------------first work----------

    --> api.php
    Route::get("Listdataapi/{id}" , [DeviceController::class,'listoddata']);

    ---> DeviceController.php
    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Device;
    use App\Models\Members;

    class DeviceController extends Controller
    {
        //
        function listoddata($id)
        {
            return Device::find($id);
        }
    }

    --------------Second work both all and number of id-------------------

    --> api.php

    Route::get("Listdataapi/{id?}" , [DeviceController::class,'listoddata']);

    --> DeviceController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Device;
    use App\Models\Members;

    class DeviceController extends Controller
    {
        //
        function listoddata($id=null)
        {
            return $id?Device::find($id):Device::all();
        }
    }



# API With Post Method
    --> Why we use POST method
    --> Setup postman for POST API
    --> Code for Post API
    --> Test API

    --> api.php

    Route::post("Listadd" , [DeviceController::class,'listdataadd']);

    -->  DeviceController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Device;
    use App\Models\Members;

    class DeviceController extends Controller
    {
        //
        function listdataadd(Request $req)
        {
            $device = new Device;
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been saved"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }

            return ["result"=>"done"];
        }
    }

    --> create modal Device.php

    <?php

    namespace App\Models;

    use Illuminate\Database\Eloquent\Factories\HasFactory;
    use Illuminate\Database\Eloquent\Model;

    class Device extends Model
    {
        use HasFactory;
        public $timestamps=false;
        public $table="device";
    }

    postman
    where first clear all
    then
    POST: ---value
    the go body-->raw ---> Text(select JSON)

    write Entery
    {
        "name":"liza",
        "member_id":12 
    }

# API with put method

    Why we use PUT method
    Setup postman for put API
    Code for Put API
    TEst APi


    Note:
    put any thing update

    api.php
    Route::put("Listupdate" , [DeviceController::class,'listdataupdate']);

    DeviceController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Device;
    use App\Models\Members;

    class DeviceController extends Controller
    {
        //
        function listdataadd(Request $req)
        {
            $device = new Device;
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been saved"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }

            return ["result"=>"done"];
        }
        function listdataupdate(Request $req){
            $device = Device::find($req->id);
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been updated"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }
        }
    }

# API With Delete Method

    --> Why we use Delete method
    --> Setup postman for Delete API
    --> Make Route, Delete Function
    --> Test API

    api.php


    Route::post("Listadd" , [DeviceController::class,'listdataadd']);
    Route::put("Listupdate" , [DeviceController::class,'listdataupdate']);
    Route::delete("Listdelete/{id}" , [DeviceController::class,'listdatadelete']);

    DeviceController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Device;
    use App\Models\Members;

    class DeviceController extends Controller
    {
        //
        function listdataadd(Request $req)
        {
            $device = new Device;
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been saved"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }

            return ["result"=>"done"];
        }
        function listdataupdate(Request $req){
            $device = Device::find($req->id);
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been updated"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }
        }
        function listdatadelete($id){
            // for delete code
            $device = Device::find($id);
            $result = $device->delete();

            if($result)
            {
                return ["result"=>"Data has been deleted"];
            }
            else{
                return  ["result"=>"Delete Operation falid"];
            }

            // for pass delete statement
            return ["Result"=>"record has been deleted".$id];
        }
    }

    Notes:

    Delete more than one...

# Search API

    --> Get method with search! Why
    --> Setup postman for API
    --> Make Route, Search Function
    --> Test API

    Notes:
    1. Data to be fetch using get
    2. http://localhost:8000/api/Listsearch/{string} to search

    --> api.php

    Route::post("Listadd" , [DeviceController::class,'listdataadd']);
    Route::put("Listupdate" , [DeviceController::class,'listdataupdate']);
    Route::delete("Listdelete/{id}" , [DeviceController::class,'listdatadelete']);
    Route::get("Listsearch/{name}" , [DeviceController::class,'listdatasearch']);

    --> DeviceController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Device;
    use App\Models\Members;

    class DeviceController extends Controller
    {
        //
        function listdataadd(Request $req)
        {
            $device = new Device;
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been saved"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }

            return ["result"=>"done"];
        }
        function listdataupdate(Request $req){
            $device = Device::find($req->id);
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been updated"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }
        }
        function listdatadelete($id){
            // for delete code
            $device = Device::find($id);
            $result = $device->delete();

            if($result)
            {
                return ["result"=>"Data has been deleted"];
            }
            else{
                return  ["result"=>"Delete Operation falid"];
            }

            // for pass delete statement
            return ["Result"=>"record has been deleted".$id];
        }
        function listdatasearch($name){
        return Device::where("name" , $name)->get();
        }
    }

    --> partial name we

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Device;
    use App\Models\Members;

    class DeviceController extends Controller
    {
        //
        function listdataadd(Request $req)
        {
            $device = new Device;
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been saved"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }

            return ["result"=>"done"];
        }
        function listdataupdate(Request $req){
            $device = Device::find($req->id);
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been updated"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }
        }
        function listdatadelete($id){
            // for delete code
            $device = Device::find($id);
            $result = $device->delete();

            if($result)
            {
                return ["result"=>"Data has been deleted"];
            }
            else{
                return  ["result"=>"Delete Operation falid"];
            }

            // for pass delete statement
            return ["Result"=>"record has been deleted".$id];
        }
        function listdatasearch($name){
        return Device::where("name" , "like", "%" .$name."%")->get();
        }
    }

# API Validation

    --> Make Route
    --> Add Validation
    --> Save and Return Result
    --> Test API

    api.php
    Route::post("Listadd" , [DeviceController::class,'listdataadd']);
    Route::put("Listupdate" , [DeviceController::class,'listdataupdate']);
    Route::delete("Listdelete/{id}" , [DeviceController::class,'listdatadelete']);
    Route::get("Listsearch/{name}" , [DeviceController::class,'listdatasearch']);
    Route::post("Listvalidate" , [DeviceController::class,'listdatavalidate']);

    DeviceController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Device;
    use App\Models\Members;

    // for validation
    use Validator;

    class DeviceController extends Controller
    {
        //
        function listdataadd(Request $req)
        {
            $device = new Device;
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been saved"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }

            return ["result"=>"done"];
        }
        function listdataupdate(Request $req){
            $device = Device::find($req->id);
            $device->name = $req->name;
            $device->member_id =$req->member_id;
            $result = $device->save();
            if($result)
            {
                return ["result"=>"Data has been updated"];
            }
            else{
                return  ["result"=>"Operation falid"];
            }
        }
        function listdatadelete($id){
            // for delete code
            $device = Device::find($id);
            $result = $device->delete();

            if($result)
            {
                return ["result"=>"Data has been deleted"];
            }
            else{
                return  ["result"=>"Delete Operation falid"];
            }

            // for pass delete statement
            return ["Result"=>"record has been deleted".$id];
        }
        function listdatasearch($name){
        return Device::where("name" , "like", "%" .$name."%")->get();
        }
        function listdatavalidate(Request $req)
        {
            $rules=array(
                "member_id"=>"required",
                "name"=>"required | max:4 "
            );
            $validator = Validator::make($req->all(),$rules);
            if($validator->fails())
            {
                // return $validator->errors();
                return response()->json($validator->errors(),401);
            }
            else{
                // return ["a"=>"x"];
                $device = new Device;
                $device->name=$req->name;
                $device->member_id=$req->member_id;
                $result = $device->save();

                if($result)
                {
                    return ["result"=>"Data has been validated"];
                }
                else{
                    return  ["result"=>"Delete Operation falid"];
                }
            }
        
        }
    }

# API with Resource

    --> Make Resources
    --> Make Route for Resource
    --> Example code with API
    --> Test API
    ////  ///
    ----------> to start server //php artisan serve
    ///   ///


    1. //we get all resource of crud

    php artisan make:controller MemberApiController --resource

    2.

    api.php in route

    <?php

    use App\Http\Controllers\MemberApiController;

    /*
    |--------------------------------------------------------------------------
    | API Routes
    |--------------------------------------------------------------------------
    |
    | Here is where you can register API routes for your application. These
    | routes are loaded by the RouteServiceProvider and all of them will
    | be assigned to the "api" middleware group. Make something great!
    |
    */

    Route::middleware('auth:sanctum')->get('/user', function (Request $request) {
        return $request->user();
    });


    Route::apiResource("AllMember", MemberApiController::class);

    3.
    Controller

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\Members;

    class MemberApiController extends Controller
    {
        /**
        * Display a listing of the resource.
        */
        public function index()
        {
            //
            return Members::all();
        }

        /**
        * Show the form for creating a new resource.
        */
        public function create()
        {
            //
        }

        /**
        * Store a newly created resource in storage.
        */
        public function store(Request $request)
        {
            //
        }

        /**
        * Display the specified resource.
        */
        public function show(string $id)
        {
            //
        }

        /**
        * Show the form for editing the specified resource.
        */
        public function edit(string $id)
        {
            //
        }

        /**
        * Update the specified resource in storage.
        */
        public function update(Request $request, string $id)
        {
            //
        }

        /**
        * Remove the specified resource from storage.
        */
        public function destroy(string $id)
        {
            //
        }
    }

    Warning: feels all the function//////////////////////////////////////////

# API auth with Sanctum

    see: official https://laravel.com/docs/10.x/sanctum

    ---> Install and Config
    ---> Migration and Controller
    ---> Example with API
    ---> Test API

    //routes api.php

    api.php

    <?php

    use Illuminate\Http\Request;
    use Illuminate\Support\Facades\Route;
    use App\Http\Controllers\dummyAPI;
    use App\Http\Controllers\DeviceController;
    use App\Http\Controllers\MemberApiController;
    use App\Http\Controllers\SacUserController;

    /*
    |--------------------------------------------------------------------------
    | API Routes
    |--------------------------------------------------------------------------
    |
    | Here is where you can register API routes for your application. These
    | routes are loaded by the RouteServiceProvider and all of them will
    | be assigned to the "api" middleware group. Make something great!
    |
    */

    Route::middleware('auth:sanctum')->get('/user', function (Request $request) {
        return $request->user();
    });

    //  use sctrum

    Route::group(['middleware' => 'auth:sanctum'], function(){
        //All secure URL's
        Route::apiResource("AllMember", MemberApiController::class);
        Route::post("Listadd" , [DeviceController::class,'listdataadd']);
        Route::put("Listupdate" , [DeviceController::class,'listdataupdate']);
        Route::delete("Listdelete/{id}" , [DeviceController::class,'listdatadelete']);
        Route::get("Listsearch/{name}" , [DeviceController::class,'listdatasearch']);
        Route::post("Listvalidate" , [DeviceController::class,'listdatavalidate']);
    });





    // user sactum

    Route::post("saclogin",[SacUserController::class,'index']);

    //make controller
    SacUserController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Models\User;
    use Illuminate\Support\Facades\Hash;

    class SacUserController  extends Controller
    {
        //
        function index(Request $request)
        {
            $user= User::where('email', $request->email)->first();
            // print_r($data);
                if (!$user || !Hash::check($request->password, $user->password)) {
                    return response([
                        'message' => ['These credentials do not match our records.']
                    ], 404);
                }
            
                $token = $user->createToken('my-app-token')->plainTextToken;
            
                $response = [
                    'user' => $user,
                    'token' => $token
                ];
            
                return response($response, 201);
        }
    }

    // include Kernal.php

    //make the models
    // user.php

    <?php

    namespace App\Models;

    // use Illuminate\Contracts\Auth\MustVerifyEmail;
    use Illuminate\Database\Eloquent\Factories\HasFactory;
    use Illuminate\Foundation\Auth\User as Authenticatable;
    use Illuminate\Notifications\Notifiable;
    use Laravel\Sanctum\HasApiTokens;

    class User extends Authenticatable
    {
        use HasApiTokens, HasFactory, Notifiable;

        /**
        * The attributes that are mass assignable.
        *
        * @var array<int, string>
        */
        protected $fillable = [
            'name',
            'email',
            'password',
        ];

        /**
        * The attributes that should be hidden for serialization.
        *
        * @var array<int, string>
        */
        protected $hidden = [
            'password',
            'remember_token',
        ];

        /**
        * The attributes that should be cast.
        *
        * @var array<string, string>
        */
        protected $casts = [
            'email_verified_at' => 'datetime',
        ];
    }

    //make Database/Seeder/UserTableSeeder.php
    <?php

    namespace Database\Seeders;

    use Illuminate\Database\Console\Seeds\WithoutModelEvents;
    use Illuminate\Database\Seeder;
    use Illuminate\Support\Facades\DB;
    use Illuminate\Support\Facades\Hash;


    class UserTableSeeder extends Seeder
    {
        /**
        * Run the database seeds.
        */
        public function run(): void
        {
            //
            DB::table('users')->insert([
                'name' => 'sika Doe',
                'email' => 'sika@doe.com',
                'password' => Hash::make('12345')
            ]);
        }
    }

    Note: See the github
    https://github.com/TrialBaseCode/laraveltxt/blob/main/laaravel_scrtrum.md
    postman work
    1. http://127.0.0.1:8000/api/saclogin-->POST
    -->raw-->JSON
    {
    //authauntic work //give login/signup/registerform
    /////// 
    {
        "email":"sika@doe.com",
        "password":12345
    }
    /////// 
    }

    we get
    {
        "user": {
            "id": 4,
            "name": "sika Doe",
            "email": "sika@doe.com"
        },
        "token": "2|gHTVqAHUbkUSIEJl9C7FrNiC0iVgwh04XgkxLTOn"
    }

    2. http://127.0.0.1:8000/api/AllMember-->GET
    Select--Headers(7) 
            ---Key               --Value
                --Authorization     --Bearer 2|gHTVqAHUbkUSIEJl9C7FrNiC0iVgwh04XgkxLTOn

    3. http://127.0.0.1:8000/api/Listsearch/S -->GET
        ---Key               --Value
                --Authorization     --Bearer 2|gHTVqAHUbkUSIEJl9C7FrNiC0iVgwh04XgkxLTOn


# Upload File with API
    --> Make Controllers & Route
    --> Setup Postman
    --> write Code for Upload file
    --> Test API and Upload File

    1.
    php artisan make:controller FileLoadController

    2.
    --> Routes
        api.php
        use App\Http\Controllers\FileLoadController;
        Route::post("fileupload" , [FileLoadController::class,'upload']);
    -->

    FileLoadController .php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;

    class FileLoadController extends Controller
    {
        //
        function upload(Request $req){
            // return ["result"=>"pass"];
            $result=$req->file("file")->store('apiDocs');
            return ["result"=>$result];
        }
    }

# Maintance Mode

    --> What is Maintenance Mode
    --> Start Maintenance Mode
    --> Bypass Maintanance Mode
    --> Display Maintanance Mode

    see site of laravel
    https://laravel.com/docs/10.x/configuration

    Notes:
    Maintance Mode
    php artisan down ->>site will be give 505 maintance mode
    php artisan up   -->> site not in mantance mode

    Need to see the website in amntance mode
    php artisan down --secret="1630542a-246b-4b66-afa1-dd72a4c43515"

    https://localhost:8000/1630542a-246b-4b66-afa1-dd72a4c43515;

