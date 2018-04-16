# RedisSourceCode
Redis3.0源码注解

---
```graphviz
digraph st2{
  fontname = "Verdana";
  fontsize = 10;
  rankdir=TB;
  
  node [fontname = "Verdana", fontsize = 10, color="skyblue", shape="record"];
  
  edge [fontname = "Verdana", fontsize = 10, color="crimson", style="solid"];
  
  st_hash_type [label="{<head>st_hash_type|(*compare)|(*hash)}"];
  st_table_entry [label="{<head>st_table_entry|hash|key|record|<next>next}"];
  st_table [label="{st_table|<type>type|num_bins|num_entries|<bins>bins}"];
  
  st_table:bins -> st_table_entry:head;
  st_table:type -> st_hash_type:head;
  st_table_entry:next -> st_table_entry:head [style="dashed", color="forestgreen"];
}
```

---
```graphviz
digraph st{
  fontname = "Verdana";
  fontsize = 10;
  rankdir = LR;
  rotate = 90;
  
  node [ shape="record", width=.1, height=.1];
  node [fontname = "Verdana", fontsize = 10, color="skyblue", shape="record"];
  
  edge [fontname = "Verdana", fontsize = 10, color="crimson", style="solid"];
  node [shape="plaintext"];
  
  st_table [label=<
      <table border="0" cellborder="1" cellspacing="0" align="left">
      <tr>
      <td>st_table</td>
      </tr>
      <tr>
      <td>num_bins=5</td>
      </tr>
      <tr>
      <td>num_entries=3</td>
      </tr>
      <tr>
      <td port="bins">bins</td>
      </tr>
      </table>
  >];
  
  node [shape="record"];
  num_bins [label=" <b1> | <b2> | <b3> | <b4> | <b5> ", height=2];
  node[ width=2 ];
  
  entry_1 [label="{<e>st_table_entry|<next>next}"];
  entry_2 [label="{<e>st_table_entry|<next>null}"];
  entry_3 [label="{<e>st_table_entry|<next>null}"];
  
  st_table:bins -> num_bins:b1;
  num_bins:b1 -> entry_1:e;
  entry_1:next -> entry_2:e;
  num_bins:b3 -> entry_3:e;
}
```
