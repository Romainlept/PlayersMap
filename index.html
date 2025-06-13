<meta charset="utf-8">
<title>Interactive Players Globe</title>
<style>
  body { margin: 0; overflow: hidden; background: #111; color: white; font-family: Arial, sans-serif; }
  svg { display: block; margin: auto; background: #222; cursor: grab; }
  svg:active { cursor: grabbing; }
  .player-circle { fill: #ff9933; stroke: #fff; stroke-width: 1.5px; cursor: pointer; }
  .player-label { fill: #fff; font-size: 12px; pointer-events: none; text-shadow: 0 0 3px black; }
  .arc { fill: none; stroke: #66ccff; stroke-width: 1.5px; opacity: 0.7; }
</style>
<body>
  <script src="https://d3js.org/d3.v7.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/topojson@3"></script>
  <script>
    const width = 960, height = 600;
    const svg = d3.select("body").append("svg").attr("width", width).attr("height", height);
    const projection = d3.geoOrthographic().scale(280).translate([width/2, height/2]).clipAngle(90);
    const path = d3.geoPath(projection);

    const globeCircle = svg.append("circle")
      .attr("fill", "#000020").attr("stroke", "#000").attr("stroke-width", 1)
      .attr("cx", width/2).attr("cy", height/2).attr("r", projection.scale());

    const players = [
      { name: "Lindbäcks Bygg AB", lat: 65.48344113783263, lng: 21.557848624839828, activity: "Pre-Fab Manufacturer", worksWith: ["Assembly Corp."] },
      { name: "Assembly Corp.", lat: 43.645031529503605, lng: -79.38289523887308, activity: "Pre-Fab Developer", worksWith: ["Lindbäcks Bygg AB"] },
      { name: "Paradigm Building Solutions Ltd.", lat: 51.14036918325003, lng: -120.1174733436564, activity: "Pre-Fab Developer", worksWith: ["Randek AB"] },
      { name: "Randek AB", lat: 56.90646671744641, lng: 12.452409652003537, activity: "Pre-Fab Manufacturer", worksWith: ["Paradigm Building Solutions Ltd."] },
    ];

    function getPlayerIndex(name) {
      return players.findIndex(p => p.name === name);
    }

    function drawMap(worldData) {
      const countries = topojson.feature(worldData, worldData.objects.countries);
      const countriesGroup = svg.append("g").attr("class", "countries");
      countriesGroup.selectAll("path").data(countries.features).join("path")
        .attr("fill", "#0a3d62").attr("stroke", "#08306b").attr("stroke-width", 0.5).attr("d", path);

      const arcsGroup = svg.append("g").attr("class", "arcs");
      const connections = [];
      players.forEach((player, i) => {
        player.worksWith.forEach(partnerName => {
          const j = getPlayerIndex(partnerName);
          if (j !== -1) connections.push([i, j]);
        });
      });
      arcsGroup.selectAll("path").data(connections).join("path").attr("class", "arc");

      const playerGroup = svg.append("g").attr("class", "players")
        .selectAll("g").data(players).join("g");
      playerGroup.append("circle").attr("class", "player-circle").attr("r", 6);
      playerGroup.append("text").attr("class", "player-label").attr("x", 8).attr("y", 4).text(d => `${d.name} (${d.activity})`);

      update();
    }

    let rotation = [0, -20];
    let lastRotation = [...rotation];

    const drag = d3.drag()
      .on("start", (event) => { lastRotation = [...rotation]; svg.style("cursor", "grabbing"); })
      .on("drag", (event) => {
        rotation[0] = (lastRotation[0] + event.dx * 0.5) % 360;
        rotation[1] = Math.min(90, Math.max(-90, lastRotation[1] - event.dy * 0.5));
        update();
      })
      .on("end", () => { svg.style("cursor", "grab"); });

    svg.call(drag);

    function update() {
      projection.rotate(rotation);
      svg.selectAll(".countries path").attr("d", path);
      svg.selectAll(".players g").attr("transform", d => {
        const coords = projection([d.lng, d.lat]);
        return coords ? `translate(${coords[0]},${coords[1]})` : null;
      });
      svg.selectAll(".arcs path").attr("d", ([i, j]) => {
        const source = [players[i].lng, players[i].lat];
        const target = [players[j].lng, players[j].lat];
        const sourcePos = projection(source);
        const targetPos = projection(target);
        if (!sourcePos || !targetPos) return null;
        const mid = d3.geoInterpolate(source, target)(0.5);
        const midPos = projection(mid);
        return d3.line()([sourcePos, midPos, targetPos]);
      });
      globeCircle.attr("cx", width/2).attr("cy", height/2).attr("r", projection.scale());
    }

    d3.json("https://unpkg.com/world-atlas@2/countries-110m.json").then(drawMap);
  </script>
</body>
