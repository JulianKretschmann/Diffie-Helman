# Diffie-Helmann
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <script>
      "use strict";

      function fDH() {
        var vg;
        var vp;
        var va;
        var vb;
        var vgA;
        var vgB;
        var vKA;
        var vKB;
        var vAusgabe;

        vg = document.getElementById("idg").value;
        vg = parseFloat(vg);

        vp = document.getElementById("idp").value;
        vp = parseFloat(vp);

        va = document.getElementById("ida").value;
        va = parseFloat(va);

        vb = document.getElementById("idb").value;
        vb = parseFloat(vb);

        vgA = Math.pow(vg, va) % vp;
        vgB = Math.pow(vg, vb) % vp;
        vKA = Math.pow(vgB, va) % vp;
        vKB = Math.pow(vgA, vb) % vp;

        vAusgabe = "Öffentlicher Schlüssel Alice: " + vgA;
        vAusgabe = vAusgabe + "<br>" + "öffentlicher Schlüssel Bob: " + vgB;
        vAusgabe =
          vAusgabe + "<br>" + "<br>" + "----------------------------" + "<br>";
        vAusgabe = vAusgabe + "<br>" + "Generierter Schlüssel K Alice: " + vKB;
        vAusgabe = vAusgabe + "<br>" + "Generierter Schlüssel K Bob: " + vKB;

        if (vp > 99) {
          vAusgabe = "  p muss kleiner 100 sein!";
        }

        document.getElementById("idAusgabe").innerHTML = vAusgabe;
      }
    </script>
    <title></title>
  </head>
  <body>
    <h1>Berechnung vom Schlüssel K nach Diffie-Hellman</h1>
    1.Alice und Bob einigen sich auf:<br />
    g = <input id="idg" type="text" value="" /><br />
    p = <input id="idp" type="text" value="" /><br /><br />
    ---------------------------------------------------------<br /><br />
    2.Alice wählt die Geheime Zahl a:<br />
    a = <input id="ida" type="text" value="" /><br />
    3. Bob wählt die Geheime Zahl b:<br />
    b = <input id="idb" type="text" value="" /><br /><br />
    <button onClick="fDH();">Berechne Schlüssel K!</button><br /><br /><br />
    <div id="idAusgabe"></div>
  </body>
</html>
