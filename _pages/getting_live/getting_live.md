---
title: Getting Live
sidebar: overview_sidebar
keywords: guidance
permalink: getting_live.html
toc: false
folder: getting_live
---

<link rel="stylesheet" href="https://unpkg.com/bootstrap-table@1.15.4/dist/bootstrap-table.min.css">
<style>.sticky-header-container {left: 3em;right: 3em;}</style>

<table 
      data-toggle="table"
      data-pagination="true"
      data-search="true"
      data-show-columns="true"
      data-show-multi-sort="true"
      data-sort-priority='[{"sortName": "github.count.forks","sortOrder":"desc"},{"sortName":"github.count.stargazers","sortOrder":"desc"}]
      data-advanced-search="true"
      data-id-table="advancedTable"
>
      <thead>
        <tr>
          <th>Item ID</th>
          <th>Item Name</th>
          <th>Item Price</th>
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
