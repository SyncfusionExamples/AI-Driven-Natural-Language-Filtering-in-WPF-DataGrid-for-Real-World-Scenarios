# AI-Driven Natural Language Filtering in WPF DataGrid for Real-World Scenarios

This sample demonstrates how to use AI-powered natural language queries to generate and apply filter predicates in a Syncfusion WPF DataGrid. Instead of manually configuring filters, users can type questions such as "Show me the male employees whose rating is more than 5" or "Find the Design Engineer whose name starts with K" and the app converts the request into the appropriate DataGrid filter conditions.

## Overview

The application combines:

- Syncfusion `SfDataGrid` for tabular data presentation and filtering
- Semantic Kernel for integrating with Azure OpenAI or OpenAI chat models
- Dynamic filter predicate generation for a real-time, AI-assisted filtering experience

This makes the grid more conversational and user-friendly, especially for non-technical users who want to query data using natural language.

## Key Features

- Natural language query-based filtering for WPF DataGrid
- AI-generated `FilterPredicate` objects based on a defined schema
- Support for multiple filter conditions such as text, date, salary, gender, and numeric ranges
- Built-in example prompts for quick testing
- Real-time filtering using Syncfusion WPF grid APIs

## Project Structure

- `MainWindow.xaml` – WPF UI with the DataGrid, search box, and action buttons
- `Behavior.cs` – Handles prompt execution, filter generation, and DataGrid filter application
- `SemanticKernalAI.cs` – Initializes the Semantic Kernel and calls Azure OpenAI
- `ViewModel.cs` – Provides employee data and sample query suggestions
- `Model.cs` – Data model definition

## Requirements

- Windows 10 / 11
- Visual Studio 2022
- .NET 8 SDK
- Syncfusion WPF components
- Azure OpenAI or OpenAI access key and model deployment

## NuGet Packages

This project references the following packages:

- `Microsoft.SemanticKernel`
- `Microsoft.Xaml.Behaviors.Wpf`
- `Newtonsoft.Json`
- `Syncfusion.SfBusyIndicator.WPF`
- `Syncfusion.SfGrid.WPF`
- `Syncfusion.SfInput.WPF`

## Setup and Configuration

1. Clone this repository.
2. Open `SmartFilterPredicates_Demo.sln` in Visual Studio 2022.
3. Restore NuGet packages.
4. Configure your Azure OpenAI details in `SemanticKernalAI.cs`:

```csharp
var builder = Kernel.CreateBuilder()
    .AddAzureOpenAIChatCompletion("Model Name", "EndPoint Link", "Key");
```

Update the values with your actual:

- model deployment name
- Azure OpenAI endpoint URL
- API key

5. Build and run the application.

## How It Works

The flow is as follows:

1. The user enters a natural language query in the input box.
2. The app builds a prompt that includes:
   - the query
   - the DataGrid model schema
   - the filter predicate structure
3. The AI model returns a JSON payload describing the filter predicate.
4. The app deserializes the response and applies it to the appropriate column in the `SfDataGrid`.
5. The grid refreshes and shows only the rows matching the generated filter.

## Example Queries

- Show the male employees whose rating is more than 5
- Show me the Engineering Manager whose sick leave hours are less than 30
- Find the Design Engineer whose name starts with K
- Show me all the employees who earn more than $2,500
- List the employees who are over 40 years old

## Notes

This sample is intended to demonstrate the concept of AI-assisted filtering in a WPF DataGrid. For production usage, you should add:

- secure handling of API keys
- validation for AI-generated filters
- robust error handling and UI feedback
- user authorization and data security checks

## License

This project is provided as a sample for educational and demonstration purposes.

## Related References

- [Syncfusion WPF DataGrid](https://www.syncfusion.com/wpf-controls/datagrid)
- [Microsoft Semantic Kernel](https://learn.microsoft.com/semantic-kernel/overview/)
- [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/overview)
