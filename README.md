## ChartJs interop with Blazor


This is a Blazor Component that wraps [ChartJS](https://github.com/chartjs/Chart.js). It was based on this repo: https://github.com/muqeet-khan/BlazorComponents


## Changelog
<details><summary>0.2.0-alpha</summary>

* Updated object model that exposes more features of ChartJs
</details>

<details><summary>0.1.0-alpha</summary>

* Initial release. 
* Support for almost all charts from ChartJs, including: LineChart, BarChart, RadarCart, Doughnut- and Pie-Chart, BubbleChart, MixedChart
</details>

## Please keep in mind that this is still a preview. Expect breaking changes during the next 2, 3 releases. I'm using this opportunity to learn Blazor.


## Prerequisites

Don't know what Blazor is? Read [here](https://github.com/aspnet/Blazor)

Prerequisites.

1. Visual Studio 15.8 or later
2. DotNetCore 2.1.402 or later


## Installation 

There's a NuGet package: https://www.nuget.org/packages/ChartJs.Blazor

Install from the command line:

```
Install-Package ChartJs.Blazor
```
or 
```
dotnet add package ChartJs.Blazor
```

## Usage

1. In you cshtlm create a new ChartJsPieChart and give it an instance of PieChartConfig ...

```html
<h2>Chart JS charts using Blazor</h2>
<div class="row">
    <button class="btn btn-primary" onclick="@UpdateChart">Update Chart </button>
</div>
<ChartJsPieChart ref="pieChartJs" Config="@pieChartConfig" Width="600" Height="300"/>
```

... make sure to create that instance
```csharp
@functions{

    private PieChartConfig pieChartConfig { get; set; }
    ChartJsPieChart pieChartJs;

    protected override void OnInit()
    {
        pieChartConfig = pieChartConfig ?? new PieChartConfig
        {
            CanvasId = "myFirstPieChart",
            Options = new PieChartOptions
            {
                Text = "Sample chart from Blazor",
                Display = true,
                Responsive = true,
                Animation = new PieChartAnimation {AnimateRotate = true, AnimateScale = true}
            },
            Data = new PieChartData
            {
                Labels = new List<string> {"A", "B", "C", "D"},
                Datasets = new List<PieChartDataset>
                {
                    new PieChartDataset
                    {
                        BackgroundColor = new[] {"#ff6384", "#55ee84", "#4463ff", "#efefef"},
                        Data = new List<int> {4, 5, 6, 7},
                        Label = "Light Red",
                        BorderWidth = 0,
                        HoverBackgroundColor = new[] {"#f06384"},
                        HoverBorderColor = new[] {"#f06384"},
                        HoverBorderWidth = new[] {1}, BorderColor = "#ffffff",
                    }
                }
            }
        };
    }
}
```

2. In your index.html add these

```html
    .
    .
    .
<body>
    <app>Loading...</app>

    <!--<script src="css/bootstrap/bootstrap-native.min.js"></script>-->
    <script src="//cdnjs.cloudflare.com/ajax/libs/Chart.js/2.7.2/Chart.min.js"></script>
    <!--<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.5.0/Chart.bundle.min.js"></script>-->
    <link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/default.min.css">
    <script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js"></script>
    <!--<script type="blazor-boot">
            </script>-->
    <script src="_framework/blazor.webassembly.js" type="text/javascript" language="javascript"></script>
    <script src="ChartJsInterop.js" type="text/javascript" language="javascript"></script>
</body>
    .
    .
    .
```


## Sample Output

Bar Chart Example:
![Charts](samples/ChartJs.Blazor.gif)

