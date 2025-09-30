# Aspirin in 3D 

Click and drag to rotate. Scroll to zoom.

```{raw} html
<div id="viewer" style="height: 420px; width: 100%; position: relative;"></div>
<script src="https://unpkg.com/3dmol/build/3Dmol-min.js"></script>
<script>
  const element = document.getElementById("viewer");
  const config = { backgroundColor: "white" };
  const viewer = $3Dmol.createViewer(element, config);
  // PubChem aspirin SDF (CID 2244)
  fetch("https://pubchem.ncbi.nlm.nih.gov/rest/pug/compound/CID/2244/SDF?record_type=3d")
    .then(r => r.text())
    .then(sdf => {
      viewer.addModel(sdf, "sdf");
      viewer.setStyle({}, {stick:{radius:0.15}, sphere:{scale:0.25}});
      viewer.addStyle({atom:"O"}, {stick:{color:"red"}});
      viewer.zoomTo(); viewer.render();
    });
</script>
