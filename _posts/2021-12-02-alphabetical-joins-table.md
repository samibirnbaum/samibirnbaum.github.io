---
layout: post
title: Rails "Joins Tables" are alphabetical
---

Imagine we have 2 models

- Area
- Lane

and you want to create a standard Joins Table with just an `area_id` and `lane_id`.

When you create the table via a migration Rails will automatically create the joins table with the folloing naming convention __in alphabetical order__ `areas_lanes`.

If you then decided to change the `Area` table to be called `Screen`, one of the things you will likely do is write a migration to change the `areas_lanes` table to be called `screens_lanes`.

You may think Rails will therefore look for a joins table called `screens_lanes` after all we have simply switched the `Area` table for a `Screen` one.

Unfortunately not, Rails will look for a table called `lanes_screens` becuase it will keep to its __alphabetical order naming convention__.

So you will need something like this:

`has_and_belongs_to_many :screens, join_table: "screens_lanes"`
