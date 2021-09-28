# MAZE-MATRIX LARAVEL 8 
## FITUR Laravel 8.x & bahasa pemrograman PHP

### VIEW
```php
<main id="main">
        <section class="labirin">
            <div class="c_box">
                <div class="section-title">
                    <h2><img class="title-img" src="{{asset('f_assets/img/labirin.jpg')}}" alt=""> GENERATE MAZE </h2>
                </div>

                <div class="container">
                    <div class="row">
                        <div class="col-lg-5 col-md-12">
                            <form action="{{route('input_angka')}}" method="post" role="form" class="php-email-form">
                                @csrf
                                <div class="form-group">
                                    <label for="exampleInputName1">Masukan angka</label>
                                    <input name="angka" id="angka" type="number" class="form-control">
                                </div>

                                <button type="submit" class="btn-sm" style="float: right;">Lihat hasil</button>
                            </form>
                        </div>
                    </div>
                </div>

            </div>
        </section>
    </main>

```
