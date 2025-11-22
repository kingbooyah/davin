
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
Ganti bagian:
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
---

Silakan edit kapan pun jika ingin menambah fitur baru!
