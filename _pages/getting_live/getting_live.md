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
      data-toggle="table"
      data-pagination="true"
      data-search="true"
      data-show-columns="true"
      data-show-multi-sort="true"
      data-sort-priority='[{"sortName": "ID","sortOrder":"desc"},{"sortName":"Name","sortOrder":"desc"}]'
      data-advanced-search="true"
      data-id-table="advancedTable"
>
      <thead>
        <tr>
          <th data-field="ID" data-sortable="true">Item ID</th>
          <th data-field="Item" data-sortable="true">Item Name</th>
          <th data-field="Price" data-sortable="true">Item Price</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
          <td>Item 1</td>
          <td>$1</td>
        </tr>
        <tr>
          <td>2</td>
          <td>Item 2</td>
          <td>$2</td>
        </tr>
      </tbody>
    </table>

<script src="https://unpkg.com/bootstrap-table@1.15.4/dist/bootstrap-table.min.js"></script>
<script src="https://unpkg.com/bootstrap-table@1.15.4/dist/extensions/multiple-sort/bootstrap-table-multiple-sort.js"></script>
<script src="https://unpkg.com/bootstrap-table@1.15.4/dist/extensions/sticky-header/bootstrap-table-sticky-header.min.js"></script>
<script src="https://unpkg.com/bootstrap-table@1.15.4/dist/extensions/toolbar/bootstrap-table-toolbar.min.js"></script>

