
## 📝 BAGIAN COUNTER
Ganti bagian:

```html
 <div class="copyright-wrapper wow fadeInUp text-center" data-wow-delay=".2s">
        <!-- Bagian Counter pengunjung -->
        <?php
        $file = "counter.txt";
        if (!file_exists($file)) {
          file_put_contents($file, 0);
        }
        $counter = file_get_contents($file);
        $counter++;
        file_put_contents($file, $counter);
        ?>
        <h6>Jumlah Pengunjung: <?php echo $counter; ?></h6>
      </div>
```

## 📝 BAGIAN database letakan di awal 
Ganti bagian paling awal sebelum html>:
```html
<!-- ============================ BAGIAN KODINGAN PHP DATABASE ========================= -->
<?php
include "koneksi.php";
if (isset($_POST['kirim'])) {
  $name = $_POST['name'];
  $email = $_POST['email'];
  $message = $_POST['message'];

  $sql = mysqli_query(
    $conn,
    "INSERT INTO konek (name, email, message) Values('$name','$email','$message')"
  );
  header("Location: index.php");
  exit;
}
?>
```
## 📝 BAGIAN koemntar pengunjung
Ganti bagian:
```html
<!-- Bagiaan komentar pengunjung -->
  <div id="coment">
    <div class=" text-center p-3 justify-content-center mb-5 ">
      <div class="card shadow p-3">
        <div class="mt-50">
          <h4>Komntar Pengunjung</h4>
        </div>
        <?php
        $result = mysqli_query($conn, "SELECT * from konek ORDER BY id DESC");
        while ($row = mysqli_fetch_assoc($result)):
          ?>

          <h6 class="mb-1 mt-5">Nama: <?= $row['name'] ?></h6>
          <h6>Pesan: <?= $row['message'] ?></h6>
        <?php endwhile; ?>
      </div>
    </div>
  </div>
```
## 📝 BAGIAN konek.php database
Ganti bagian:
```html
<?php
$conn = mysqli_connect("localhost", "root", "", "komentar") or die("ggl");
?>


atau bisa juga pake
```html
<?php foreach (mysqli_query($conn, "SELECT * FROM konek ORDER BY id DESC") as $row): ?>
  <h6>Nama: <?= $row['name'] ?></h6>
  <h6>Pesan: <?= $row['message'] ?></h6>
<?php endforeach; ?>

```
---

```html
<!-- Fungsi Tambah Komentar -->
<?php
include "koneksi.php";
if (isset($_POST['kirim'])) {
    date_default_timezone_set("Asia/Jakarta");
    $timestamp = time();
    $nama = $_POST['nama'];
    $email = $_POST['email'];
    $komentar = $_POST['komentar'];
    $tanggal = date('Y-m-d H:i:s', $timestamp);

    $sql = mysqli_query($koneksi, "INSERT INTO komentar VALUES('','$nama','$email','$komentar','$tanggal')");
    echo "<script>alert('Komentar berhasil dikirim');window.location.href='index.php';</script>";
}
?>
```
```html
<?php
$koneksi = mysqli_connect("localhost", "root", "", "nama_database");

if (mysqli_connect_errno()) {
    echo "Gagal koneksi ke MySQL: " . mysqli_connect_error();
    exit;
}
?>
Silakan edit kapan pun jika ingin
menambah fitur baru!
```

