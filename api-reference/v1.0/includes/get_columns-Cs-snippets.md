
```Cs

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var workbookTableColumn = await graphClient.Me.Drive.Items["{id}"].Workbook.Tables["{id|name}"].Columns
	.Request()
	.Skip(5)
	.Top(5)
	.GetAsync();

```