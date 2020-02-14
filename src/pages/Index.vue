<template>
  <div>
  <a href="http://localhost:8080/week"><h3>Электронный журнал</h3></a>
    <span >Школа № 30</span>
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