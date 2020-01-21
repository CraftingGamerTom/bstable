# BSTable

## Overview

BSTable Copyright (C) 2020 Thomas Rokicki (CraftingGamerTom)

Javascript library to make HMTL tables editable, using Bootstrap. Based on the javascript library bootstable which enabled editing of tables per page - however did not allow for different event handling per table.
Thank you t-edson for your contributions to the open source community and enabling me to create this library on top of your work.

![BSTable](https://github.com/CraftingGamerTom/bstable/blob/master/bstable.png?raw=true "BSTable")

"BSTable" is a javascript library (plugin), that converts a HTML static bootstrap table to an editable table. 
A table is made editable, it inserts several buttons to perform the edit actions.

Actions includes:

* Edit fields.
* Remove rows.
* Add rows. (requires an additional button defined manually)

Dependencies:

* Jquery
* Bootstrap
* Font Awesome

Bootstrap and Font Awesome is required to format the table correctly, control edits, and to draw icons.

No database / API connection is included. The library was designed to work offline. Handle events by defining custom functions within the options variable.

## How to use

Create the BSTable object (example uses all default options)

    var editableTable = new BSTable("table-id-of-table-to-make-editable");  // Define the table
    editableTable.init();                                                   // Initialize the editable table

Create the BSTable with examples of setting common options

    var editableTable = new BSTable("table-id-of-table-to-make-editable", {
      editableColumns: "1,2,3",           // Make columns 1, 2, & 3 editable
      $addButton: $('#add-new-button'),   // Set the add new row button
      onEdit:function() {                 // Set function to call when editing complete
        // call API here.
      },
      advanced: {                         
          columnLabel: ''                 // Set the column label to have no text
      }
    });
    editableTable.init();

Refresh the table (Call if the table dynamically updates)

    editableTable.refresh();

## Parameters

            editableColumns: null,          // Index to editable columns. If null all td will be editable. Ex.: "1,2,3,4,5"
            $addButton: null,               // Jquery object of "Add" button
            onEdit: function() {},          // Called after edition
            onBeforeDelete: function() {},  // Called before deletion
            onDelete: function() {},        // Called after deletion
            onAdd: function() {},           // Called when added a new row
            
            advanced: {                     // Do not override advanced unless you know what youre doing
                columnLabel: 'Actions',
                buttonHTML: `<div class="btn-group pull-right">
                        <button id="bEdit" type="button" class="btn btn-sm btn-default" onclick="rowEdit(this);">
                            <span class="fa fa-edit" > </span>
                        </button>
                        <button id="bElim" type="button" class="btn btn-sm btn-default" onclick="rowElim(this);">
                            <span class="fa fa-trash" > </span>
                        </button>
                        <button id="bAcep" type="button" class="btn btn-sm btn-default" style="display:none;" onclick="rowAcep(this);">
                            <span class="fa fa-check-circle" > </span>
                        </button>
                        <button id="bCanc" type="button" class="btn btn-sm btn-default" style="display:none;" onclick="rowCancel(this);">
                            <span class="fa fa-times-circle" > </span>
                        </button>
                    </div>`
            }
