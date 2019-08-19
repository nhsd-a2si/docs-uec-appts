---
title: Getting Live
sidebar: overview_sidebar
keywords: guidance
permalink: getting_live.html
toc: false
folder: getting_live
---

<link rel="stylesheet" href="https://unpkg.com/bootstrap-table@1.15.4/dist/bootstrap-table.min.css">
<table 
      id="table"
      data-toggle="table"
      data-pagination="true"
      data-search="true"
      data-show-columns="true"
      data-show-multi-sort="true"
      data-sort-priority='[{"sortName": "ID","sortOrder":"desc"},{"sortName":"Capability","sortOrder":"desc"}]'
      data-advanced-search="true"
      data-id-table="advancedTable"
      data-search-accent-neutralise="true">
      <thead>
        <tr>
          <th data-field="ID" data-sortable="true">Item ID</th>
          <th data-field="Capability" data-sortable="true">Capability</th>
          <th data-field="Supplier" data-sortable="true">Supplier</th>
          <th data-field="Status" data-sortable="true">Status</th>
          <th data-field="Date" data-sortable="true">Date</th>
          <th data-field="Dependencies" data-sortable="true">Dependencies</th>
          <th data-field="Comments" data-sortable="true">Comments</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
          <td>Book an appointment - GP</td>
          <td>Advanced</td>
          <td>Complete</td>
          <td>July 2019</td>          
          <td>None</td>
          <td>Ability to search and book an appointment</td>
        </tr>  
        <tr>
          <td>IC24</td>
          <td>Testing</td>
          <td>19th August 2019</td>
          <td>None</td>
          <td>Ability to search and book an appointment</td>
        </tr>
        <tr>
          <td>Cleric</td>
          <td>Development</td>
          <td>October 2019</td>
          <td>None</td>
          <td>Ability to search and book an appointment</td>
        </tr>
      </tbody>
    </table>

<script src="https://unpkg.com/bootstrap-table@1.15.4/dist/bootstrap-table.min.js"></script>
<script src="https://unpkg.com/bootstrap-table@1.15.4/dist/extensions/multiple-sort/bootstrap-table-multiple-sort.js"></script>
<script src="https://unpkg.com/bootstrap-table@1.15.4/dist/extensions/sticky-header/bootstrap-table-sticky-header.min.js"></script>
<script src="https://unpkg.com/bootstrap-table@1.15.4/dist/extensions/toolbar/bootstrap-table-toolbar.min.js"></script>
<script src="https://unpkg.com/bootstrap-table@1.15.4/dist/extensions/accent-neutralise/bootstrap-table-accent-neutralise.min.js"></script>
<script>
       var $table = $('#table')
      $table.on('load-success.bs.table column-switch.bs.table page-change.bs.table search.bs.table', function () {
            $table.bootstrapTable('mergeCells', {index: 0,
        field: 'ID',
        colspan: 1,
        rowspan: 3})
      })
</script>
