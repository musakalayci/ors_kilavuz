******
Türler
******

.. toctree::
   :maxdepth: 2
   
   turler/yapıtasları
   turler/sayac
   turler/tur 
   turler/kalıp
   turler/yalın 
   turler/ortak 

Buraya kadar işlemler ve işlevlerle ilgilendik 
ama tüm bunlar anlamlı yapılandırılmış veri olmadan tamamen anlamsız 
kalıyor. 

Bu bölümde Örs dilinin türlere yaklaşımını ele alacağız. 

---------------------

.. graphviz:: 

   graph D {
   subgraph cluster_0 { 
      label="Türler";
      türler [label="tür" fixedsize=true fillcolor=red style=filled shape=circle,width=3];
      subgraph cluster_1 
      {
        label="Gerçek Türler"
        yapıtaşları [label="yapıtaşları" fixedsize=true shape=circle,width=3];
        ortak [label="ortak"];

        yalın [label="yalın"];
      }
      subgraph cluster_2 
      {
        label="yapıtaşları";
        subgraph cluster_3 
        {
           label="konum";
           iş  [label="işlemler"];
           şey [label="şey"];
           mimari -- şey;
        }
        subgraph cluster_4 
        {
           label="sayılar"; 
           mimari  [label="mimari"];
           subgraph cluster_5 
           {
              label="tam sayılar";
              t8   [label = "t8"];
              t16  [label = "t16"];
              t32  [label = "t32"];
              t64  [label = "t64"];
              t128 [label = "t128"];
              tam  [label = "tam"]; 
              t8  -- t16;
              t16 -- t32;
              t32 -- t64;
              t64 -- t128;
              t32 -- tam;
           }
           subgraph cluster_6 
           {
              label="doğal sayılar";
              d8    [label = "d8"];
              d16   [label = "d16"];
              d32   [label = "d32"];
              d64   [label = "d64"];
              d128  [label = "d128"];
              doğal [label = "doğal"]; 
              d8  -- d16;
              d16 -- d32;
              d32 -- d64;
              d64 -- d128;
              d32 -- doğal;
           }
           subgraph cluster_7 
           {
              label="ondalık sayılar";
              o32     [label = "o32"];
              o64     [label = "o64"];
              o128    [label = "o128"];
              ondalık [label = "ondalık"]; 
              o32 -- o64;
              o64 -- o128;
              o64 -- ondalık;
           }
        }
        ondalık -- yapıtaşları;
        doğal   -- yapıtaşları;
        tam     -- yapıtaşları;
        şey     -- yapıtaşları;
      }
      subgraph cluster_8 
      { 
        label="sanal türler";
        sayaç [label="sayaç"];
        kalıp [label="kalıp"];
        tam         -- sayaç;
      }
       iş  -- türler;
       türler -- ortak;
       türler -- yapıtaşları;
       türler -- kalıp; 
       türler -- yalın;
       sayaç       -- türler;
     }
   }

