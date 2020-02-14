<template>
  <div>
<<<<<<< HEAD
  <a href="http://localhost:8080/week"><h3>Электронный журнал</h3></a>
    <span >Школа № 30</span>
=======
  <router-link to="/week"><h3>Электронный журнал</h3></router-link>
      <span >Школа № 30</span>
    <q-btn @click="scan">Сканировать QR</q-btn>
>>>>>>> a9a7c9255d534afc06e583cda6bfe93d5377e4a1
  </div>
</template>

<script>
export default{
methods:{
 scan(){
   cordova.plugins.barcodeScanner.scan(
      function (result) {
          alert("We got a barcode\n" +
                "Result: " + result.text + "\n" +
                "Format: " + result.format + "\n" +
                "Cancelled: " + result.cancelled);
      },
      function (error) {
          alert("Scanning failed: " + error);
      }
   );
 }
}
}
  
</script>