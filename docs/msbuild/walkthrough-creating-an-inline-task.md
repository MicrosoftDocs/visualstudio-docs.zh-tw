---
title: 逐步解說：建立內嵌工作 | Microsoft Docs
description: 逐步解說如何在專案檔中建立內嵌的 MSBuild 工作，而不需要建立個別的元件來裝載工作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f8a4e39d38f81684b5d090152ec720d45438b3b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907453"
---
# <a name="walkthrough-create-an-inline-task"></a>逐步解說：建立內嵌工作

MSBuild 工作通常是透過編譯實作 <xref:Microsoft.Build.Framework.ITask> 介面的類別來建立。 從 .NET Framework 4 版開始，您可以在專案檔中建立內嵌工作。 您不必建立個別的組件來裝載工作。 如需詳細資訊，請參閱 [內嵌](../msbuild/msbuild-inline-tasks.md)工作。

 本逐步解說示範如何建立並執行這些內嵌工作：

- 沒有輸入或輸出參數的工作。

- 有一個輸入參數，沒有輸出參數的工作。

- 有兩個輸入參數，一個傳回 MSBuild 屬性之輸出參數的工作。

- 有兩個輸入參數，一個傳回 MSBuild 項目之輸出參數的工作。

若要建立並執行作業，請使用 Visual Studio 和「Visual Studio 命令提示字元視窗」，如下所示︰

1. 使用 Visual Studio 建立 MSBuild 專案檔。

2. 修改 Visual Studio 中的專案檔以建立內嵌工作。

3. 使用「命令提示字元視窗」來建置專案並檢查結果。

## <a name="create-and-modify-an-msbuild-project"></a>建立和修改 MSBuild 專案

 Visual Studio 專案系統是以 MSBuild 為基礎。 因此，您可以使用 Visual Studio 建立組建專案檔。 在本節中，您將建立 Visual C# 專案檔。 (您可以改為建立 Visual Basic 專案檔。 在本教學課程的內容中，這兩個專案檔之間的差異非常小)。

#### <a name="to-create-and-modify-a-project-file"></a>建立並修改專案檔

1. 在 Visual Studio 中，使用 c # **Windows Forms 應用程式** 範本建立新專案。 在 [名稱]  方塊中，輸入 `InlineTasks`。 輸入方案的 [位置]，例如 *D:\\*。 確認已選取 [為方案建立目錄]、已取消選取 [加入至原始檔控制]，且 [方案名稱] 為 **InlineTasks**。

3. 按一下 [確定] 以建立專案檔。

3. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **InlineTasks** ] 專案節點，然後按一下 **[卸載專案**]。

4. 再次以滑鼠右鍵按一下專案節點，然後按一下 [編輯 InlineTasks.csproj]。

     該專案檔隨即出現在程式碼編輯器中。

## <a name="add-a-basic-hello-task"></a>加入基本的 Hello 工作

 現在，將顯示 "Hello, world!" 之訊息的基本工作加入到專案檔 也加入預設 TestBuild 目標來叫用工作。

#### <a name="to-add-a-basic-hello-task"></a>加入基本的 Hello 工作

1. 在根 `Project` 節點，將 `DefaultTargets` 屬性變更為 `TestBuild`。產生的 `Project` 節點應該類似以下範例：

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. 將下列的內嵌工作與目標加入到專案檔中的 `</Project>` 標記之前。

   ```xml
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup />
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, "Hello, world!");
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Hello />
   </Target>
   ```

3. 儲存專案檔。

   此程式碼會建立名為 Hello 且沒有參數、參考或指示詞的內嵌工作 `Using` 。 Hello 工作僅包含一行程式碼，它會在預設記錄裝置 (通常是在主控台視窗) 上顯示 hello 訊息。

### <a name="run-the-hello-task"></a>執行 Hello 工作

 使用「命令提示字元視窗」執行 MSBuild，以建構 Hello 工作並處理叫用它的 TestBuild 目標。

##### <a name="to-run-the-hello-task"></a>執行 Hello 工作

1. 按一下 [開始]，按一下 [所有程式]，接著尋找 **Visual Studio Tools** 資料夾，然後按一下 [Visual Studio 命令提示字元]。

2. 在 [**命令提示字元] 視窗** 中，找出包含專案檔的資料夾，在此案例中為 *D:\InlineTasks\InlineTasks \\*。

3. 輸入 **msbuild** 而不搭配命令參數，然後按 **enter**。 根據預設，這會建立 *InlineTasks .csproj* 檔案，並處理叫用 Hello 工作的預設目標 TestBuild。

4. 檢查「命令提示字元視窗」中的輸出。 您應該會看到下列這一行：

    `Hello, world!`

   > [!NOTE]
   > 如果您沒有看到 hello 訊息，請嘗試重新儲存專案檔，然後執行 Hello 工作。

   藉由交替使用程式碼編輯器和「命令提示字元視窗」，您可以變更專案檔並快速查看結果。

## <a name="define-the-echo-task"></a>定義 Echo 工作

 建立接受字串參數，並會在預設記錄裝置上顯示字串的內嵌工作。

#### <a name="to-define-the-echo-task"></a>定義 Echo 工作

1. 在程式碼編輯器中，使用下列程式碼取代 Hello 工作和 TestBuild 目標。

   ```xml
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Text Required="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, Text);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Echo Text="Greetings!" />
   </Target>
   ```

2. 在 [ **命令提示字元] 視窗** 中，輸入 **msbuild** 而不搭配命令參數，然後按 **enter**。 根據預設，這會處理叫用 Echo 工作的預設目標 TestBuild。

3. 檢查「命令提示字元視窗」中的輸出。 您應該會看到下列這一行：

    `Greetings!`

   此程式碼會定義名為 Echo，且僅有一個必要的輸入參數 Text 的內嵌工作。 根據預設，參數屬於類型 System.String。 當 TestBuild 目標叫用 Echo 工作時，會設定 Text 參數的值。

## <a name="define-the-adder-task"></a>定義 Adder 工作

 建立會將兩個整數參數加總，且將其總和以 MSBuild 屬性發出的內嵌工作。

#### <a name="to-define-the-adder-task"></a>定義 Adder 工作

1. 在程式碼編輯器中，使用下列程式碼取代 Echo 工作和 TestBuild 目標。

   ```xml
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <A ParameterType="System.Int32" Required="true" />
       <B ParameterType="System.Int32" Required="true" />
       <C ParameterType="System.Int32" Output="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         C = A + B;
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Adder A="4" B="5">
       <Output PropertyName="Sum" TaskParameter="C" />
     </Adder>
     <Message Text="The sum is $(Sum)" Importance="High" />
   </Target>
   ```

2. 在 [ **命令提示字元] 視窗** 中，輸入 **msbuild** 而不搭配命令參數，然後按 **enter**。 根據預設，這會處理叫用 Echo 工作的預設目標 TestBuild。

3. 檢查「命令提示字元視窗」中的輸出。 您應該會看到下列這一行：

    `The sum is 9`

   此程式碼會定義名為 Adder，且有兩個必要整數輸入參數 A 和 B，以及一個整數輸出參數 C 的內嵌工作。Adder 工作會將兩個輸入參數加總，並在輸出參數中傳回總和。 總和會以 MSBuild 屬性 `Sum` 發出。 當 TestBuild 目標叫用 Adder 工作時，會設定輸入參數的值。

## <a name="define-the-regx-task"></a>定義 RegX 工作

 建立一個內嵌工作，該內嵌工作會接受項目群組和規則運算式，且傳回所有具備符合運算式之檔案內容的項目清單。

#### <a name="to-define-the-regx-task"></a>定義 RegX 工作

1. 在程式碼編輯器中，使用下列程式碼取代 Adder 工作和 TestBuild 目標。

   ```xml
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Expression Required="true" />
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />
     </ParameterGroup>
     <Task>
       <Using Namespace="System.Text.RegularExpressions"/>
       <Code Type="Fragment" Language="cs">
   <![CDATA[
         if (Files.Length > 0)
         {
           Result = new TaskItem[Files.Length];
           for (int i = 0; i < Files.Length; i++)
           {
             ITaskItem item = Files[i];
             string path = item.GetMetadata("FullPath");
             using(StreamReader rdr = File.OpenText(path))
             {
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)
               {
                 Result[i] = new TaskItem(item.ItemSpec);
               }
             }
           }
         }
   ]]>
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <RegX Expression="public|protected" Files="@(Compile)">
       <Output ItemName="MatchedFiles" TaskParameter="Result" />
     </RegX>
     <Message Text="Input files: @(Compile)" Importance="High" />
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />
   </Target>
   ```

2. 在 [ **命令提示字元] 視窗** 中，輸入 **msbuild** 而不搭配命令參數，然後按 **enter**。 根據預設，這會處理會叫用 RegX 工作的預設目標 TestBuild。

3. 檢查「命令提示字元視窗」中的輸出。 您應該會看到下列這幾行：

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   此程式碼定義名為 RegX，且具備下列三個參數的內嵌工作：

- `Expression` 是必要的字串輸入參數，其值為要比對的規則運算式。 在此範例中，運算式符合字組「公用」或「受保護」。

- `Files` 是必要的項目清單輸入參數，其值為要搜尋以比對之檔案的清單。 在此範例中，`Files` 設定為 `Compile` 項目，其中會列出專案原始程式檔。

- `Result` 是輸出參數，其值為具備符合規則運算式之內容的檔案清單。

  當 TestBuild 目標叫用 RegX 工作時，會設定輸入參數的值。 RegX 工作會讀取每個檔案，並傳回符合規則運算式之檔案的清單。 這份清單會以 `Result` 輸出參數傳回，會以 MSBuild 項目 `MatchedFiles` 發出。

### <a name="handle-reserved-characters"></a>處理保留字元

 MSBuild 剖析器會以 XML 的方式處理內嵌工作。 以 XML 形式保留意義的字元，例如 " \<" and "> "，會以 xml 而非 .net 原始程式碼的形式來偵測和處理。 若要在程式碼運算式中包含保留字元 (例如 `Files.Length > 0`)，請撰寫 `Code` 元素，讓其內容包含在 CDATA 運算式中，如下所示︰

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  if (Files.Length > 0)
  {
      // Your code goes here.
  }
  ]]>
</Code>
```

## <a name="see-also"></a>另請參閱

- [內嵌工作](../msbuild/msbuild-inline-tasks.md)
- [工作](../msbuild/msbuild-tasks.md)
- [目標](../msbuild/msbuild-targets.md)
