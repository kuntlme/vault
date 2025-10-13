---
tags:
  - coding
  - alloy
Topics:
  - YAML
---
**Key value**
name: kuntal
first_name: Kuntal
**Comment**
`# this is a demo inline comment`
chai_reciepe:
  base: milk (use two space, don't use tab)
  milk: whole_milk

chai_name: Masala chai
description: "chai with cardamom, ginger"


brewing_instruction: |
  boil water
  add tea leaves
  add milk

brewing_instruction: >
  boil water
  add tea leaves
  add milk

`| or > ` these are used for foldable code


`numbers`
cups_per_day: 3
cups_per_day_two: 0FF2FF

`boolean`
is_not: true
add_suger: yes
add_salt: no
instant: on
check: off

sweetner: null
alternative_milk: ~ (this is also mean `null`)

`timeststamps`
time: 2025-01-15
local: 2025-01-15 08:30:01


`collections or array or list`
spices: 
  `- spices`
  `- cloves`
  `- black_pepper`

`# spices: [cardamom, ginger, cloves]`
steeping_times: [3, 2, 1]

chai_categories:
  `- name: Traditional`
    varities:
       - Masala chai

`reusable code`
default_chai_base: &default_base :luc_arrow_big_left:this called anchor or alias
  tea: 2gm
  water: 200ml
  time: 5

:luc_arrow_big_up: this make a base that I can reuse

morning_chai:
  `<<: *default_base
  milk: 100ml`

`explicit data type`
zip_code: !!str 12345
count: !!int "123"
unique_spices: !!set
  ? cardamon
  ? ginger
  ? cloves