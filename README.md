# MAZE-MATRIX LARAVEL 8 
## FITUR Laravel 8.x & bahasa pemrograman PHP

### 1. VIEW
#### a. View Input Angka

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

#### b. View Hasil Matrix Maze
```php
<div class="container">
                    <div class="row">
                        <div class="col-lg-12 col-md-12">

                            <?php
                            $terkecil = $min;
                            $terbesar = $max;
                            $second_first = $min + 1;
                            $second_last = $max - 1;
                            $kel = $min + 4;
                            ?>

                            <table style="margin:5px auto">
                                <?php for ($i = 1; $i <= $inputan; $i++) { ?>


                                    <?php if ($i == $min) { ?>
                                        <!-- JIKA BARIS PERTAMA -->
                                        <tr>
                                            <td><?php $i ?></td>
                                        </tr>
                                        <tr>
                                            <?php for ($j = 1; $j <= $inputan; $j++) { ?>
                                                <td>
                                                    <h2 style="color: <?= ($j == $second_first) ? "white" : "black"; ?>">@</h2>
                                                </td>
                                            <?php } ?>
                                        </tr>
                                        <!-- JIKA BARIS PERTAMA -->
                                    <?php } elseif ($i == $max) { ?>
                                        <!-- JIKA BARIS TERAKHIR -->
                                        <tr>
                                            <td><?php $i ?></td>
                                        </tr>
                                        <tr>

                                            <?php for ($j = 1; $j <= $inputan; $j++) { ?>
                                                <td>
                                                    <h2 style="color: <?= ($j == $second_last) ? "white" : "black"; ?>">@</h2>
                                                </td>
                                            <?php } ?>
                                        </tr>
                                        <!-- JIKA BARIS TERAKHIR -->
                                    <?php } elseif ($i % 2 == 0) { ?>
                                        <!-- BARIS DENGAN BILANGAN GENAP -->
                                        <tr>
                                            <td><?php $i ?></td>
                                        </tr>
                                        <tr>

                                            <?php for ($j = 1; $j <= $inputan; $j++) { ?>
                                                <td>
                                                    <h2 style="color: <?= ($j != $min and $j != $max) ? "white" : "black"; ?>">@</h2>
                                                </td>
                                            <?php } ?>
                                        </tr>
                                        <!-- /BARIS DENGAN BILANGAN GENAP -->
                                    <?php } elseif ($i % 2 !== 0 & $i % 4 !== 1) { ?>
                                    <!-- BARIS DENGAN BILANGAN GENAP TAPI JIKA DI BAGI BILANGAN 4 TIDAK MEMILIKI SISA 1 -->
                                        <tr>
                                            <td><?php $i ?></td>
                                        </tr>
                                        <tr>

                                            <?php for ($j = 1; $j <= $inputan; $j++) { ?>
                                                <td>
                                                    <h2 style="color: <?= ($j == $second_last) ? "white" : "black"; ?>">@</h2>
                                                </td>
                                            <?php } ?>
                                        </tr>
                                        <!-- /BARIS DENGAN BILANGAN GENAP TAPI JIKA DI BAGI BILANGAN 4 TIDAK MEMILIKI SISA 1 -->
                                    <?php } elseif ($i % 4 == 1) { ?>
                                    <!-- BARIS DENGAN  BILANGAN YANG DI BAGI 4 MEMILIKI SISA 1 -->
                                        <tr>
                                            <td><?php $i ?></td>
                                        </tr>
                                        <tr>

                                            <?php for ($j = 1; $j <= $inputan; $j++) { ?>
                                                <td>
                                                    <h2 style="color: <?= ($j == $second_first) ? "white" : "black"; ?>">@</h2>
                                                </td>
                                            <?php } ?>
                                        </tr>
                                        <!-- /BARIS DENGAN  BILANGAN YANG DI BAGI 4 MEMILIKI SISA 1 -->
                                    <?php } ?>

                                <?php } ?>
                            </table>
                        </div>
                    </div>
                </div>
```


### 1. CONTROLLER
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class C_maze extends Controller
{
    public function index()
    {
        return view('labirin');
    }

    public function input_angka(Request $request)
    {
        $angka = $request->angka;
        $kosong = [];
        for ($i = 1; $i <= $angka; $i++) {
            $kosong[] = $i;
        }
        $data = [
            "angka" => $kosong,
            "max" => $angka,
            "min" => 1,
            "inputan" => $angka,
        ];
        return view('hasil_labirin', $data);
    }
}
```


