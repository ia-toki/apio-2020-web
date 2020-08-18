---
layout: full-single-page-md
title: Official Results
key: results
---

The official results will be announced on the [closing ceremony](/closing.html) and will be updated here afterwards.

<form>
  <label for="filter">Filter By Country: </label>
  <select id="filter" style="width:auto">
  </select>
</form>
<table id="results"></table>

<script>
  var country_index = 4;
  var medal_index = 6;
  var data = [];
  var table_el = document.getElementById("results");
  var filter_el = document.getElementById("filter");
  var countries = [ "All Countries", "ARM", "AUS", "AZE", "BGD", "CHN", "GEO", "HKG", "IND",
                    "IDN", "IRN", "ISR", "JPN", "KAZ", "KOR", "KGZ", "MAC",
                    "MYS", "MNG", "NZL", "PSE", "PHL", "RUS", "SAU", "SGP",
                    "LKA", "SYR", "TWN", "TJK", "THA", "TUR", "TKM", "UZB", "VNM"];
  
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
      var data = allTextLines[i].split(',');
      lines.push(data);
    }

    return lines;
  }

  function onFilterChange(e) {
    table_el.querySelectorAll(".medal").forEach(tr => {
      var contents = tr.children;
      if (e.target.value == "All Countries" || e.target.value == contents[country_index].textContent) {
        tr.style.removeProperty("display");
      } else {
        tr.style.display = "none";
      }
    });
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

  populateFilter();

  httpGetAsync("/results.csv", function(allText) {
    data = processCSV(allText);
    populateTable(table_el, data);
  });
</script>