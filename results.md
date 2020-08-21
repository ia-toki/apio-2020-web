---
layout: full-single-page-md
title: Official Results
key: results
---

The official results was announced on the [closing ceremony](/closing.html).

<form>
  <label for="filter">Filter By Country: </label>
  <select id="filter" style="width:auto">
  </select>
</form>
<table id="results"></table>

<script>
  const country_index = 1;
  const medal_index = 3;
  var data = [];
  var table_el = document.getElementById("results");
  var filter_el = document.getElementById("filter");
  var countries = [ "All Countries" ];
  
  function onlyUnique(value, index, self) { 
    return self.indexOf(value) === index;
  }

  function populateCountries() {
    countries = countries.concat(data.map(c => c[country_index])
                .slice(1).filter(onlyUnique).sort());
  }
  
  function h (parent, tag) {
    var el = document.createElement(tag);
    parent.append(el);
    return el;
  }

  function httpGetAsync(theUrl, callback)
  {
    var xmlHttp = new XMLHttpRequest();
    xmlHttp.onreadystatechange = function() { 
      if (xmlHttp.readyState == 4 && xmlHttp.status == 200)
        callback(xmlHttp.responseText);
    }
    xmlHttp.open("GET", theUrl, true); // true for asynchronous 
    xmlHttp.send(null);
  }

  function processCSV(allText) {
    var allTextLines = allText.split(/\r\n|\n/);
    var lines = [];

    for (var i=0; i<allTextLines.length; i++) {
      var data = allTextLines[i].split('\t');
      lines.push(data);
    }

    return lines;
  }

  function onFilterChange(e) {
    populateTable(
      table_el, 
      [data[0]].concat(data.slice(1).filter(c => 
        e.target.value === "All Countries" 
        || e.target.value === c[country_index]))
    );
  }

  function populateFilter() {
    filter_el.addEventListener("change", onFilterChange);
    for (var i = 0; i<countries.length; i++) {
      var option = h(filter_el, "option");
      option.textContent = countries[i];
      option.value = countries[i];
    }
  }

  function populateTable(table, data) {
    table.innerHTML = "";
    var thead = h(table, "thead");
    var thead_tr = h(thead, "tr");
    for (var j=0; j<data[0].length; j++) {
      var th = h(thead_tr, "th");
      th.textContent = data[0][j];
    }
    var tbody = h(table, "tbody");
    for (var i=1; i<data.length; i++) {
      var tbody_tr = h(tbody, "tr");
      tbody_tr.classList.add("medal");
      tbody_tr.classList.add("medal-" + data[i][medal_index].toLowerCase().replace(" ", "_"));
      for (var j=0; j<data[i].length; j++) {
        var td = h(tbody_tr, "td");
        td.textContent = data[i][j];
      }
    }
  }

  httpGetAsync("/results.tsv", function(allText) {
    data = processCSV(allText);
    populateCountries();
    populateFilter();
    populateTable(table_el, data);
  });
</script>
