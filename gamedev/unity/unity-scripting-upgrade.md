---
title: 在 Unity 中使用 .NET 4.x
description: 瞭解如何在 Unity 中使用 .NET 4.x。 啟用 .NET 4.x 腳本執行時間。 利用 .NET 相容性。 檢查新的語法和語言功能。
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: how-to
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.workload:
- unity
ms.openlocfilehash: c1b745e4a1da85324b2dc73e30bebb873e2d0720
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559806"
---
# <a name="using-net-4x-in-unity"></a>在 Unity 中使用 .NET 4.x

C# 和 .NET (以 Unity 指令碼為基礎的技術) 持續接收到更新，因為 Microsoft 一開始是在 2002 年發行它們。 但是，Unity 開發人員可能察覺不到穩定新增至 C# 語言和.NET Framework 的新功能。 原因是在 Unity 2017.1 之前，Unity 使用 .NET 3.5 對等指令碼執行階段，因而遺失數年的更新。

隨著 Unity 2017.1 的發行，Unity 引進將其指令碼執行階段升級至 .NET 4.6 (C# 6 相容版本) 的實驗性版本。 在 Unity 2018.1 中，不再將 .NET 4.x 對等執行階段視為實驗性，現在會將舊版 .NET 3.5 對等執行階段視為舊版本。 而隨著 Unity 2018.3 的發行，Unity 預測會將已升級的指令碼執行階段設為預設選取項目，甚至進一步更新為 C# 7。 如需本藍圖的詳細資訊和最新更新，請閱讀 Unity 的[部落格文章](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)，或瀏覽其 [Experimental Scripting Previews 論壇](https://forum.unity.com/forums/experimental-scripting-previews.107/)。 在此同時，請參閱下列各節，來深入了解 .NET 4.x 指令碼執行階段現在可用的新功能。

## <a name="prerequisites"></a>先決條件

* [Unity 2017.1 或更新版本](https://unity3d.com/) (建議使用 2018.2)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>在 Unity 中啟用 .NET 4.x 指令碼執行階段

若要在 Unity 中啟用 .NET 4.x 指令碼執行階段，請採取下列步驟：

1. 選取 [編輯] > [專案設定] > [Player] \(播放程式\)，以在 Unity Inspector 中開啟 PlayerSettings。

1. 在 [組態] 標題下，按一下 [Scripting Runtime Version] \(指令碼執行階段版本\) 下拉式清單，然後選取 [.NET 4.x Equivalent] \(.NET 4.x 對等項目\)。 系統將提示您重新啟動 Unity。

![選取 [.NET 4.x Equivalent] \(.NET 4.x 對等項目\)](media/vs/vstu-scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>選擇 .NET 4.x 或 .NET Standard 2.0 設定檔

在您切換到 .NET 4.x 對等指令碼執行階段之後，即可使用 PlayerSettings 中的下拉式功能表 ([編輯] > [專案設定] > [Player] \(播放程式\)) 指定 [Api Compatibility Level] \(API 相容性層級\)。 有兩個選項：

* **.NET Standard 2.0**。 此設定檔符合 .NET Foundation 所發行的 [.NET Standard 2.0 設定檔](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md)。 Unity 建議將 .NET Standard 2.0 用於新專案。 這小於適用於大小受限平台的 .NET 4.x。 此外，Unity 致力於跨 Unity 所支援的所有平台支援此設定檔。

* **.Net** 4.x。 此設定檔提供對最新 .NET 4 API 的存取。 它包含 .NET Framework 類別庫中所有可用的程式碼，同時支援 .NET Standard 2.0 設定檔。 如果您的專案需要 .NET Standard 2.0 設定檔中未包含的 API 部分，則請使用 .NET 4.x 設定檔。 不過，Unity 的所有平台上可能都不支援此 API 的某些部分。

您可以在 Unity 的[部落格文章](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)中深入了解這些選項。

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>在使用 .NET 4.x API 相容性層級時新增組件參考

使用 [Api Compatibility Level] \(API 相容性層級\) 下拉式清單中的 .NET Standard 2.0 設定時，可參考和使用 API 設定檔中的所有組件。 不過，使用較大的 .NET 4.x 設定檔時，預設不會參考 Unity 隨附的部分組件。 若要使用這些 API，您必須手動新增組件參考。 您可以在 Unity 編輯器安裝的 **MonoBleedingEdge/lib/mono** 目錄中檢視 Unity 隨附的組件：

![MonoBleedingEdge 目錄](media/vs/vstu-monobleedingedge.png)

例如，如果您使用 .NET 4.x 設定檔，並且想要使用 `HttpClient`，則必須新增 System.Net.Http.dll 的組件參考。 否則，編譯器會通知您遺漏組件參考：

![遺漏組件參考](media/vs/vstu-missing-reference.png)

Visual Studio 會在每次開啟 Unity 專案時重新產生其 .csproj 和 .sln 檔案。 因此，您無法直接在 Visual Studio 中新增組件參考，因為它們會在重新開啟專案時遺失。 相反地，必須使用名為 **csc** 的特殊文字檔：

1. 在 Unity 專案的根 **資產** 目錄中，建立名為 **csc** 的新文字檔。

1. 在空文字檔中的第一行，輸入：`-r:System.Net.Http.dll`，然後儲存檔案。 您可以將 "System.Net.Http.dll" 取代為任何可能遺漏參考的內含組件。

1. 重新啟動 Unity 編輯器。

## <a name="taking-advantage-of-net-compatibility"></a>利用 .NET 相容性

除了新 C# 語法和語言功能之外，.NET 4.x 指令碼執行階段還可讓 Unity 使用者存取與舊版 .NET 3.5 指令碼執行階段不相容之 .NET 套件的超大型程式庫。

### <a name="add-packages-from-nuget-to-a-unity-project"></a>將套件從 NuGet 新增至 Unity 專案

[NuGet](https://www.nuget.org/) 是適用於 .NET 的套件管理員。 NuGet 整合到 Visual Studio。 不過，Unity 專案需要新增 NuGet 套件的特殊程序。 這是因為當您在 Unity 中開啟專案時，會重新產生其 Visual Studio 專案檔，並復原所需的組態。 若要將套件從 NuGet 新增至 Unity 專案，請執行下列作業：

1. 瀏覽 NuGet 以找到您要新增的相容套件 (.NET Standard 2.0 或 .NET 4.x)。 此範例示範如何將 [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/) (使用 JSON 的熱門套件) 新增至 .NET Standard 2.0 專案。

1. 按一下 [ **下載** ] 按鈕：

    ![[下載] 按鈕](media/vs/vstu-nuget-download.png)

1. 找到下載的檔案，並將副檔名從 **.nupkg** 變更為 **.zip**。

1. 在 ZIP 檔案內，瀏覽至 **lib/netstandard2.0** 目錄，並複製 **Newtonsoft.Json.dll** 檔案。

1. 在 Unity 專案的根 **Assets** 資料夾中，建立名為 **Plugins** 的新資料夾。 Plugins 是 Unity 中的特殊資料夾名稱。 如需詳細資訊，請參閱 [Unity 文件](https://docs.unity3d.com/Manual/Plugins.html)。

1. 將 **Newtonsoft.Json.dll** 檔案貼入 Unity 專案的 **Plugins** 目錄。

1. 在 Unity 專案的 **Assets** 目錄中，建立名為 **link.xml** 的檔案，並新增下列 XML。  這將確保 Unity 的位元組程式碼去除程序不會在匯出至 IL2CPP 平台時移除必要資料。  此步驟是這個程式庫特有的步驟時，以類似方式使用反映的其他程式庫可能會發生問題。  如需詳細資訊，請參閱本主題的 [Unity 文件](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html)。

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

一切準備就緒後，您現在可以使用 Json.NET 套件。

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

這個簡單範例使用沒有相依性的程式庫。 NuGet 套件依賴其他 NuGet 套件時，您需要手動下載這些相依性，並使用相同的方式將其新增至專案。

## <a name="new-syntax-and-language-features"></a>新的語法和語言功能

使用更新過的指令碼執行階段可讓 Unity 開發人員存取 C# 6 和一堆新語言功能和語法。

### <a name="auto-property-initializers"></a>Auto 屬性初始設定式

在 Unity 的 .NET 3.5 指令碼執行階段中，auto-property 語法可讓您輕鬆地快速定義未初始化的屬性，但必須在指令碼的其他位置初始化。 現在使用 .NET 4.x 執行階段，就可以初始化同一行的 auto-properties：

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>字串插補

使用較舊的 .NET 3.5 執行階段，字串串連需要冗長的必要語法。 現在有了 .NET 4.x 執行時間， [ `$` 字串插補](/dotnet/csharp/language-reference/tokens/interpolated)功能可讓您以更直接易懂的語法將運算式插入字串中：

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>運算式主體成員

使用 .NET 4.x 執行階段中可用的較新 C# 語法，[Lambda 運算式](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)可以取代函數主體，讓它們更為簡潔：

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

您也可以在唯讀屬性中使用運算式主體成員︰

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>以工作為基礎的非同步模式 (TAP)

[非同步程式設計](/dotnet/csharp/async)允許執行耗時作業，而不會讓您的應用程式變得無回應。 此功能也可讓您的程式碼先等待耗時作業完成，再繼續執行根據這些作業結果的程式碼。 例如，您可以等待載入檔案或完成網路作業。

在 Unity 中，通常會使用[協同程式](https://docs.unity3d.com/Manual/Coroutines.html)完成非同步程式設計。 不過，從 C# 5 之後，在 .NET 開發中慣用的非同步程式設計方法已是搭配使用 `async` 和 `await` 關鍵字與 [System.Threading.Task](/dotnet/api/system.threading.tasks.task)的[工作非同步模式 (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)。 總而言之，在 `async` 函數中，您可以 `await` (等待) 工作完成，而不需要封鎖更新應用程式的其餘部分：

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

TAP 是一個複雜主題，而開發人員應該考慮其 Unity 特定細微差別。 因此，TAP 不是 Unity 中協同程式的通用取代項目；不過，它是另一個要運用的工具。 此功能的範圍不在本文範圍內，但在下面提供一些一般最佳做法和秘訣。

#### <a name="getting-started-reference-for-tap-with-unity"></a>利用 Unity 開始使用 TAP 的參考

這些秘訣可協助您在 Unity 中開始使用 TAP：

* 要等候的非同步函式應該有傳回型別 [`Task`](/dotnet/api/system.threading.tasks.task) 或 [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1) 。
* 傳回工作的非同步函數應該在其名稱附加尾碼 **"Async"**。 "Async" 尾碼有助於指出應該一律等候函數。
* 只會使用可從傳統同步程式碼引發 async 函數之函數的 `async void` 傳回型別。 這類函數本身無法等候，而且不應該在其名稱中有 "Async" 尾碼。
* 根據預設，Unity 使用 UnitySynchronizationContext 確保在主要執行緒上執行 async 函數。 Unity API 無法在主要執行緒外部存取。
* 您可以使用和等方法在背景執行緒上執行工作 [`Task.Run`](/dotnet/api/system.threading.tasks.task.run) [`Task.ConfigureAwait(false)`](/dotnet/api/system.threading.tasks.task.configureawait) 。 這項技術適用於卸載主要執行緒的耗費資源作業，以提高效能。 不過，使用背景執行緒可能會導致很難偵錯的問題 (例如[競爭條件](https://wikipedia.org/wiki/Race_condition))。
* Unity API 無法在主要執行緒外部存取。
* Unity WebGL 組建不支援使用執行緒的工作。

#### <a name="differences-between-coroutines-and-tap"></a>協同程式與 TAP 的差異

協同程式與 TAP / async-await 之間有一些重要差異：

* 協同程式無法傳回值，但 `Task<TResult>` 可以。
* 您無法在 try-catch 陳述式中放置 `yield`，這讓協同程式很難處理錯誤。 不過，try-catch 可與 TAP 搭配運作。
* 在未衍生自 MonoBehaviour 的類別中，無法使用 Unity 的協同程式功能。 TAP 很適合在這類類別中執行非同步程式設計。
* 此時，Unity 不建議使用 TAP 完全取代協同程式。 分析是知道其中一種方法與任何指定專案另一種方法之特定結果的唯一方式。

> [!NOTE]
> 截自 Unity 2018.2，完全不支援偵錯含中斷點的 async 方法；不過，[Unity 2018.3 預期會有此功能](https://twitter.com/jbevain/status/900043560665235456)。

### <a name="nameof-operator"></a>nameof 運算子

`nameof` 運算子會取得變數、型別或成員的字串名稱。 有些需要使用 `nameof` 的情況是記錄錯誤，以及取得列舉的字串名稱：

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>呼叫端資訊屬性

[呼叫端資訊屬性](/dotnet/csharp/programming-guide/concepts/caller-information)提供方法呼叫端的相關資訊。 您必須針對要與「呼叫端資訊」屬性搭配使用的每個參數提供預設值：

```csharp
private void Start ()
{
    ShowCallerInfo("Something happened.");
}
public void ShowCallerInfo(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    Debug.Log($"message: {message}");
    Debug.Log($"member name: {memberName}");
    Debug.Log($"source file path: {sourceFilePath}");
    Debug.Log($"source line number: {sourceLineNumber}");
}
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>using static

[using static](/dotnet/csharp/language-reference/keywords/using-static) 可讓您使用靜態函數，而不需要鍵入其類別名稱。 如果您需要使用相同類別中的數個靜態函數，則使用 using static 可以節省空間和時間：

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>IL2CPP 考量

將遊戲匯出至 iOS 這類平台時，Unity 將使用其 IL2CPP 引擎以將 IL「轉換」為 C++ 程式碼，而且接著會使用目標平台的原生編譯器來編譯 C++ 程式碼。 在此情節中，有幾項不支援的 .NET 功能，例如反映的組件和 `dynamic` 關鍵字的用法。 雖然您可以利用自己的程式碼控制這些功能的使用，但是請注意，使用未以 Unity 和 IL2CPP 撰寫的協力廠商 DLL 和 SDK 可能會發生問題。 如需本主題的詳細資訊，請參閱 Unity 網站上的 [Scripting Restrictions](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) (指令碼限制) 文件。

此外，如上述 Json.NET 範例所述，Unity 將嘗試在 IL2CPP 匯出程序期間去除未使用的程式碼。  雖然這通常不是問題，但使用反映的程式庫可能會不小心去除將在執行時間呼叫的屬性或方法，而無法在匯出時判斷。  若要修正這些問題，請將 **link.xml** 檔案新增至專案，而專案包含不要對其執行去除程序的組件和命名空間清單。  如需完整詳細資料，請參閱[位元組程式碼去除的 Unity 文件](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html)。

## <a name="net-4x-sample-unity-project"></a>.NET 4.x 範例 Unity 專案

此範例包含數個 .NET 4.x 功能範例。 您可以在 [GitHub](https://github.com/Microsoft/unity-scripting-upgrade) 下載專案或檢視原始程式碼。

## <a name="additional-resources"></a>其他資源

* [Unity Blog - Scripting Runtime Improvements in Unity 2018.2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) (Unity 部落格 - Unity 2018.2 中的指令碼執行階段改善)
* [C# 的歷程記錄](/dotnet/csharp/whats-new/csharp-version-history)
* [C# 6 的新功能](/dotnet/csharp/whats-new/csharp-6)
* [Asynchronous programming in Unity, Using Coroutine and TAP](/archive/blogs/appconsult/unity-coroutine-tap-en-us) (Unity 中使用協同程式和 TAP 的非同步程式設計)
* [Async-Await Instead of Coroutines in Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/) (Unity 2017 中的 Async-Await 而非協同程式)
* [Unity Forum - Experimental Scripting Previews](https://forum.unity.com/forums/experimental-scripting-previews.107/) (Unity 論壇 - Experimental Scripting Previews)