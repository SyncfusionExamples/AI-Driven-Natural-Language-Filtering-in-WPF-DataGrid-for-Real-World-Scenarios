# AI-Driven Natural Language Filtering in WPF Data Grid for Real-World Scenarios

This sample demonstrates how to use Azure OpenAI or OpenAI with Microsoft Semantic Kernel to convert natural-language queries into Syncfusion `WPF Data Grid` filter predicates. Instead of manually creating filter conditions, users can ask questions in plain English and the app generates the corresponding filter logic automatically.

## Overview

The application combines:

- Syncfusion `WPF Data Grid` for tabular data display and filtering
- Microsoft Semantic Kernel for chat completion and prompt orchestration
- Azure OpenAI or OpenAI for understanding natural-language queries
- Dynamic predicate generation to apply real-time filters to the grid

This makes data exploration more conversational and user-friendly, especially for non-technical users who want to filter records without writing filter logic manually.

## Key Features

- Natural language query-based filtering for WPF Data Grid
- AI-generated `FilterPredicate` objects based on the data model schema
- Support for a range of conditions such as text, date, number, and range-based filters
- Example queries for quick testing
- Real-time filtering through the Syncfusion WPF grid APIs
- Built-in employee dataset to simulate real-world scenarios

## Project Structure

The solution contains the following key files:

- `MainWindow.xaml` – WPF UI for the grid, query box, and action buttons
- `MainWindow.xaml.cs` – Application startup and main window logic
- `Behavior.cs` – Handles the prompt, AI response processing, and filter application
- `SemanticKernalAI.cs` – Creates the Semantic Kernel and calls Azure OpenAI
- `ViewModel.cs` – Provides employee data and sample query suggestions
- `Model.cs` – Data model used by the grid
- `App.xaml` and `App.xaml.cs` – Application-level startup configuration
- `SmartFilterPredicates_Demo.csproj` – Project file with NuGet dependencies
- `SmartFilterPredicates_Demo.sln` – Visual Studio solution file

## Requirements

- Windows 10 / 11
- Visual Studio 2022
- .NET 8 SDK
- Syncfusion WPF components
- Azure OpenAI or OpenAI access with a valid deployment/model name

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
3. Restore the NuGet packages.
4. Update your Azure OpenAI or OpenAI settings in `SemanticKernalAI.cs`:

```csharp
var builder = Kernel.CreateBuilder()
    .AddAzureOpenAIChatCompletion("Model Name", "EndPoint Link", "Key");
```

Replace the placeholder values with your actual:

- model deployment name
- Azure OpenAI endpoint URL
- API key

5. Build and run the application.

## How It Works

The flow is as follows:

1. The user enters a natural language query in the text box.
2. The app prepares a prompt that includes the query, the current model schema, and the grid data structure.
3. Semantic Kernel sends the prompt to Azure OpenAI or OpenAI.
4. The model returns a JSON payload that describes the filter conditions.
5. The response is deserialized into one or more `AIFilterPredicate` objects.
6. Each predicate is validated and applied to the matching column in the `WPF Data Grid`.
7. The grid refreshes and displays only the filtered records.

## Example Queries

The sample includes several built-in query suggestions, including:

- Show the male employees whose rating is more than 5
- Show me the Engineering Manager whose sick leave hours are less than 30
- Show me all the employees who earn more than $2,500
- Find the Design Engineer whose name starts with K
- List the employees who are over 40 years old
- Show me the female employees who are over 45 years old

## Notes

This sample is intended to demonstrate AI-assisted filtering in a WPF Data Grid. For production use, consider adding:

- secure handling of API keys and endpoint values
- validation of AI-generated filter output
- robust exception handling and user messages
- authorization and data protection checks in your application layer

## Related References

- [Syncfusion WPF DataGrid](https://www.syncfusion.com/wpf-controls/datagrid)
- [Microsoft Semantic Kernel](https://learn.microsoft.com/semantic-kernel/overview/)
- [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/overview)

## Sample Scenario

The sample uses an employee dataset with fields such as:

- `EmployeeID`
- `Name`
- `Gender`
- `Title`
- `BirthDate`
- `Salary`
- `Rating`
- `ContactID`
- `SickLeaveHours`

This enables queries such as filtering by title, salary, age, gender, rating, and date ranges.

This project is provided as a sample for educational and demonstration purposes.
