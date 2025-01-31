## Minecraft load time benchmark


---

<p align="center" style="font-size:160%;">
MC total load time:<br>
535.41 sec
<br>
<sup><sub>(
8:55 min
)</sub></sup>
</p>

<br>


<p align="center">
<img src="https://quickchart.io/chart?w=400&h=30&c={
  type: 'horizontalBar',
  data: {
    datasets: [
      {label:      'MODS:', data: [301.09]},
      {label: 'FML stuff:', data: [234.32]}
    ]
  },
  options: {
    scales: {
      xAxes: [{display: false,stacked: true}],
      yAxes: [{display: false,stacked: true}],
    },
    elements: {rectangle: {borderWidth: 2}},
    legend: {display: false,},
    plugins: {datalabels: {color: 'white',formatter: (value, context) =>
      [context.dataset.label, value].join(' ')
    }}
  }
}"/>
</p>

<br>

# Mods Loading Time
<p align="center">
<img src="https://quickchart.io/chart?w=400&h=300&c={
  type: 'outlabeledPie',
  options: {
    cutoutPercentage: 25,
    plugins: {
      legend: !1,
      outlabels: {
        stretch: 5,
        padding: 1,
        text: (v,i)=>[
          v.labels[v.dataIndex],' ',
          (v.percent*1000|0)/10,
          String.fromCharCode(37)].join('')
      }
    }
  },
  data: {...
`
436e17  26.02s Had Enough Items;
3C6315  16.00s Had Enough Items (Plugins);
516fa8  15.82s Ender IO;
813e81  12.14s OpenComputers;
5161a8   0.79s CraftTweaker2;
495797   8.79s CraftTweaker2 (Script Loading);
8f3087   9.09s Forge Mod Loader;
a651a8   8.80s IndustrialCraft 2;
8f304e   7.10s Astral Sorcery;
cd922c   6.20s NuclearCraft;
8c2ccd   5.37s Immersive Engineering;
213664   5.11s Forestry;
6e175e   4.91s Recurrent Complex;
538f30   4.15s Animania;
308f53   4.02s Village Names;
8f4d30   3.89s Open Terrain Generator;
a86e51   3.73s Extra Utilities 2;
436e17   3.70s Integrated Dynamics;
308f7e   3.44s Quark: RotN Edition;
ba3eb8   3.27s Cyclic;
649e21   3.09s OpenBlocks;
3e68ba   3.03s AE2 Unofficial Extended Life;
444444  75.63s 43 Other mods;
333333  59.88s 175 'Fast' mods (load 1.0s - 0.1s);
222222   7.13s 207 'Instant' mods (load %3C 0.1s)
`
    .split(';').reduce((a, l) => {
      l.match(/(\w{6}) *(\d*\.\d*)s (.*)/)
      .slice(1).map((a, i) => [[String.fromCharCode(35),a].join(''), parseFloat(a), a][i])
      .forEach((s, i) => 
        [a.datasets[0].backgroundColor, a.datasets[0].data, a.labels][i].push(s)
      );
      return a
    }, {
      labels: [],
      datasets: [{
        backgroundColor: [],
        data: [],
        borderColor: 'rgba(22,22,22,0.3)',
        borderWidth: 1
      }]
    })
  }
}"/>
</p>

<br>

# Top Mods Details (except JEI, FML and Forge)
<p align="center">
<img src="https://quickchart.io/chart?w=400&h=450&c={
  options: {
    scales: {
      xAxes: [{stacked: true}],
      yAxes: [{stacked: true}],
    },
    plugins: {
      datalabels: {
        anchor: 'end',
        align: 'top',
        color: 'white',
        backgroundColor: 'rgba(46, 140, 171, 0.6)',
        borderColor: 'rgba(41, 168, 194, 1.0)',
        borderWidth: 0.5,
        borderRadius: 3,
        padding: 0,
        font: {size:10},
        formatter: (v,ctx) => 
          ctx.datasetIndex!=ctx.chart.data.datasets.length-1 ? null
            : [((ctx.chart.data.datasets.reduce((a,b)=>a- -b.data[ctx.dataIndex],0)*10)|0)/10,'s'].join('')
      },
      colorschemes: {
        scheme: 'office.Damask6'
      }
    }
  },
  type: 'bar',
  data: {...(() => {
    let a = { labels: [], datasets: [] };
`
1: Construction;
2: Loading Resources;
3: PreInitialization;
4: Initialization;
5: InterModComms$IMC;
6: PostInitialization;
7: LoadComplete;
8: ModIdMapping
`
    .split(';')
      .map(l => l.match(/\d: (.*)/).slice(1))
      .forEach(([name]) => a.datasets.push({ label: name, data: [] }));
`
                           1      2      3      4      5      6      7      8  ;
Ender IO               |  1.55|  0.01|  4.06|  0.55|  3.37|  0.14|  0.00|  6.15;
OpenComputers          |  0.45|  0.02|  8.26|  3.21|  0.20|  0.00|  0.00|  0.00;
CraftTweaker2          |  0.62|  0.00|  4.17|  0.01|  0.00|  4.76|  0.01|  0.00;
IndustrialCraft 2      |  0.70|  0.02|  6.97|  0.85|  0.00|  0.27|  0.00|  0.00;
Astral Sorcery         |  0.26|  0.01|  4.63|  1.63|  0.00|  0.57|  0.00|  0.00;
NuclearCraft           |  0.57|  0.01|  3.97|  0.42|  0.00|  1.17|  0.00|  0.06;
Immersive Engineering  |  0.84|  0.01|  1.12|  1.07|  0.00|  2.33|  0.00|  0.00;
Forestry               |  0.40|  0.01|  3.24|  1.03|  0.00|  0.42|  0.00|  0.00;
Recurrent Complex      |  0.26|  0.01|  0.66|  0.90|  0.00|  3.09|  0.00|  0.00;
Animania               |  0.31|  0.00|  3.22|  0.11|  0.00|  0.51|  0.00|  0.00;
Village Names          |  0.11|  0.00|  3.72|  0.19|  0.00|  0.00|  0.00|  0.00;
Open Terrain Generator |  0.04|  0.01|  0.00|  3.84|  0.00|  0.00|  0.00|  0.00
`
    .split(';').slice(1)
      .map(l => l.split('|').map(s => s.trim()))
      .forEach(([name, ...arr], i) => {
        a.labels.push(name);
        arr.forEach((v, j) => a.datasets[j].data[i] = v)
      }); return a
  })()}
}"/>
</p>

<br>

# TOP JEI Registered Plugis
<p align="center">
<img src="https://quickchart.io/chart?w=700&c={
  options: {
    elements: { rectangle: { borderWidth: 1 } },
    legend: false
  },
  type: 'horizontalBar',
    data: {...(() => {
      let a = {
        labels: [], datasets: [{
          backgroundColor: 'rgba(0, 99, 132, 0.5)',
          borderColor: 'rgb(0, 99, 132)',
          data: []
        }]
      };
`
  2.43: cofh.thermalexpansion.plugins.jei.JEIPluginTE;
  1.46: jeresources.jei.JEIConfig;
  1.29: com.github.sokyranthedragon.mia.integrations.jer.JeiJerIntegration$1;
  0.98: com.rwtema.extrautils2.crafting.jei.XUJEIPlugin;
  0.89: crazypants.enderio.machines.integration.jei.MachinesPlugin;
  0.76: ic2.jeiIntegration.SubModule;
  0.75: mezz.jei.plugins.vanilla.VanillaPlugin;
  0.66: knightminer.tcomplement.plugin.jei.JEIPlugin;
  0.55: nc.integration.jei.NCJEI;
  0.54: com.buuz135.thaumicjei.ThaumcraftJEIPlugin;
  0.49: com.buuz135.industrial.jei.JEICustomPlugin;
  0.37: crazypants.enderio.base.integration.jei.JeiPlugin;
  0.25: ninjabrain.gendustryjei.GendustryJEIPlugin;
  0.24: rustic.compat.jei.RusticJEIPlugin;
  0.23: net.bdew.jeibees.BeesJEIPlugin;
  4.14: Other 127 Plugins
`
        .split(';')
        .map(l => l.split(':'))
        .forEach(([time, name]) => {
          a.labels.push(name);
          a.datasets[0].data.push(time)
        })
        ; return a
    })()
  }
}"/>
</p>

<br>

# FML Stuff
<p align="center">
<img src="https://quickchart.io/chart?w=500&h=400&c={
  options: {
    rotation: Math.PI,
    cutoutPercentage: 55,
    plugins: {
      legend: !1,
      outlabels: {
        stretch: 5,
        padding: 1,
        text: (v)=>v.labels
      },
      doughnutlabel: {
        labels: [
          {
            text: 'FML stuff:',
            color: 'rgba(128, 128, 128, 0.5)',
            font: {size: 18}
          },
          {
            text: [234.32,'s'].join(''),
            color: 'rgba(128, 128, 128, 1)',
            font: {size: 22}
          }
        ]
      },
    }
  },
  type: 'outlabeledPie',
  data: {...(() => {
    let a = {
      labels: [],
      datasets: [{
        backgroundColor: [],
        data: [],
        borderColor: 'rgba(22,22,22,0.3)',
        borderWidth: 2
      }]
    };
`
993A00   1.50s Loading sounds;
994400   1.57s Loading Resource - SoundHandler;
994F00  44.37s ModelLoader: blocks;
995900  15.36s ModelLoader: items;
996300  14.97s ModelLoader: baking;
996D00   1.97s Applying remove recipe actions;
997700   0.12s Applying remove furnace recipe actions;
998200   0.92s Indexing ingredients;
998C00   9.02s Indexing ingredients;
444444 144.52s Other
`
    .split(';')
      .map(l => l.match(/(\w{6}) *(\d*\.\d*)s (.*)/))
      .forEach(([, col, time, name]) => {
        a.labels.push([name, ' ', time, 's'].join(''));
        a.datasets[0].data.push(parseFloat(time));
        a.datasets[0].backgroundColor.push([String.fromCharCode(35), col].join(''))
      })
      ; return a
  })()}
}"/>
</p>

<br>
