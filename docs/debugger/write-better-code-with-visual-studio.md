---
title: 偵錯技術和工具
description: 通過使用 Visual Studio 修復異常、修復錯誤和改進代碼，編寫更好的代碼，減少錯誤
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302025"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>調試技術和工具，説明您編寫更好的代碼

修復代碼中的 Bug 和錯誤可能是一項耗時（有時甚至是令人沮喪的）任務。 學習如何有效地調試需要時間，但像 Visual Studio 這樣的強大 IDE 可以使您的工作輕鬆得多。 IDE 可以説明您修復錯誤並更快地調試代碼，而不僅僅是這樣，它還可以説明您用更少的 Bug 編寫更好的代碼。 本文的目的是讓您全面瞭解"錯誤修復"過程，以便您知道何時使用代碼分析器、何時使用調試器、如何修復異常以及如何編寫意圖代碼。 如果您已經知道需要使用調試器，請參閱[首先查看調試器](../debugger/debugger-feature-tour.md)。

在本文中，我們將討論利用 IDE 提高編碼會話的效率。 我們涉及幾個任務，例如：

* 利用 IDE 的代碼分析器準備用於調試的代碼

* 如何修復異常（執行階段錯誤）

* 如何通過編碼意圖（使用斷言）來最小化 Bug

* 何時使用調試器

為了演示這些任務，我們展示了一些在嘗試調試應用時會遇到的最常見的錯誤和錯誤類型。 儘管示例代碼為 C#，但概念資訊通常適用于 Visual Studio 支援C++、視覺基礎語言、JavaScript 和其他語言（除非另有說明）。 螢幕擷取畫面則使用 C# 表示。

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>創建包含一些錯誤和錯誤的示例應用

以下代碼有一些可以使用 Visual Studio IDE 修復的錯誤。 此處的應用程式是一個簡單的應用程式，用於類比從某些操作獲取 JSON 資料、將資料反序列化到物件以及使用新資料更新簡單列表。

若要建立應用程式：

1. 您必須安裝 Visual Studio 並安裝 **.NET Core 跨平臺開發**或 **.NET 桌面開發**工作負載，具體取決於要創建的應用類型。

    如果您尚未安裝 Visual Studio，請轉到 Visual [Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面以免費安裝它。

    如果您需要安裝工作負載，但已有視覺化工作室，請按一下 **"工具** > **獲取工具和功能**"。 Visual Studio 安裝程式即會啟動。 選擇 **.NET 核心跨平臺開發**或 **.NET 桌面開發**工作負載，然後選擇 **"修改**"。

1. 開啟 Visual Studio。

    ::: moniker range=">=vs-2019"
    在啟動視窗中，選擇 **"創建新專案**"。 在搜索框中鍵入**主控台**，然後選擇**主控台應用 （.NET 核心）** 或**主控台應用程式 （.NET 框架）**。 選擇 [下一步]****。 鍵入專案名稱，如**Console_Parse_JSON，** 然後按一下"**創建**"。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂部功能表列中，選擇 **"檔** > **新專案** > **"。** 在 **"新建專案**"對話方塊的左側窗格中，在**Visual C#** 下，選擇**主控台應用**，然後在中間窗格中選擇**主控台應用 （.NET Core）** 或**主控台應用 （.NET Framework）。** 鍵入**Console_Parse_JSON等**名稱，然後按一下 **"確定**"。
    ::: moniker-end

    如果您沒有看到**主控台應用 （.NET Core）** 或**主控台應用 （.NET Framework）** 專案範本，請**Tools** > 轉到**工具獲取工具和功能**，這將打開視覺化工作室安裝程式。 選擇 **.NET Core 跨平臺開發**或 **.NET 桌面開發**工作負載，然後選擇 **"修改**"。

    Visual Studio 隨即建立主控台專案，並出現在右窗格的 [方案總管] 中。

1. 將專案*Program.cs*檔中的預設代碼替換為下面的示例代碼。

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>找到紅色和綠色的波浪！

在嘗試啟動示例應用並運行調試器之前，請檢查代碼編輯器中的代碼有紅色和綠色波浪。 這些表示 IDE 的代碼分析器標識的錯誤和警告。 紅色波浪是編譯時間錯誤，必須先修復這些錯誤，然後才能運行代碼。 綠色波浪是警告。 儘管您通常可以在不修復警告的情況下運行應用，但它們可能是 Bug 的來源，並且通常通過調查它們來節省自己的時間和麻煩。 如果您喜歡清單視圖，這些警告和錯誤也會顯示在 **"錯誤清單"** 視窗中。

在示例應用中，您將看到需要修復的幾個紅色波浪，以及一個要查看的綠色波浪。 這是第一個錯誤。

![顯示為紅色波浪形的錯誤](../debugger/media/write-better-code-red-squiggle.png)

要修復此錯誤，您將查看 IDE 的另一個功能，該功能由燈泡圖示表示。

## <a name="check-the-light-bulb"></a>檢查燈泡！

第一個紅色波浪表示編譯時的錯誤。 將滑鼠懸停在它上，然後```The name `Encoding` does not exist in the current context```您看到消息。

請注意，此錯誤在左下角顯示一個燈泡圖示。 與![螺絲刀圖示螺絲刀圖示](../ide/media/screwdriver-icon.png)一起，燈泡圖示![燈泡圖示](../ide/media/light-bulb-icon.png)表示快速操作，可説明您修復或重構代碼內聯。 燈泡表示*應*修復的問題。 螺絲刀適用于您可能選擇修復的問題。 使用第一個建議的修復程式通過按一下左側的 **"系統.文本**"來解決此錯誤。

![使用燈泡修復代碼](../debugger/media/write-better-code-missing-include.png)

按一下此專案時，Visual Studio 會在`using System.Text`*Program.cs*檔的頂部添加語句，紅色波浪形將消失。 （如果您不確定建議的修復程式將執行什麼操作，請先在應用修復程式之前選擇右側的 **"預覽更改"** 連結。

前面的錯誤通常是通過向代碼添加新`using`語句來解決的。 有幾個常見的類似錯誤，例如```The type or namespace `Name` cannot be found.```這些類型的錯誤可能指示缺少程式集引用（按右鍵專案，選擇**添加** > **引用**），拼寫錯誤的名稱，或缺少需要添加的庫（對於 C#，按右鍵專案並選擇 **"管理 NuGet 包**"）。

## <a name="fix-the-remaining-errors-and-warnings"></a>修復剩餘的錯誤和警告

在此代碼中還有一些波浪形。 在這裡，您將看到一個常見的類型轉換錯誤。 將滑鼠懸停在波浪上時，您會看到代碼正在嘗試將字串轉換為 int，除非您添加顯式代碼進行轉換，否則不支援 int。

![類型轉換錯誤](../debugger/media/write-better-code-conversion-error.png)

由於代碼分析器無法猜測您的意圖，因此這次沒有燈泡可以説明您。 要修復此錯誤，您需要瞭解代碼的意圖。 在此示例中，不難看出該`points`值應該是一個數位（整數）值，因為您正在嘗試添加到`points``totalpoints`中。

要修復此錯誤，從中`points`更改`User`類的成員：

```csharp
[DataMember]
internal string points;
```

變更為以下程式碼：

```csharp
[DataMember]
internal int points;
```

代碼編輯器中的紅色波浪線消失。

接下來，將滑鼠懸停在`points`資料成員聲明中的綠色波浪形上。 代碼分析器告訴您該變數永遠不會分配值。

![未分配變數的警告訊息](../debugger/media/write-better-code-warning-message.png)

通常，這表示需要修復的問題。 但是，在示例應用中，您實際上是在反序列化過程中將資料`points`存儲在變數中，然後將該值添加到`totalpoints`資料成員中。 在此示例中，您知道代碼的意圖，並可以安全地忽略警告。 但是，如果要消除該警告，可以替換以下代碼：

```csharp
item.totalpoints = users[i].points;
```

取代為這個：

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

綠色的波浪消失了。

## <a name="fix-an-exception"></a>修復異常

修復了所有紅色波浪，並解決了所有綠色波浪，或者至少被調查，就可以啟動調試器並運行應用了。

按**F5** （**調試>開始調試**）或"調試工具列中![開始調試"開始調試](../debugger/media/dbg-tour-start-debugging.png "[偵錯]")。 **Start Debugging**

此時，示例應用將引發異常`SerializationException`（執行階段錯誤）。 也就是說，應用程式會阻塞它嘗試序列化的資料。 由於您在偵錯模式下啟動應用（已連接調試器），調試器的異常協助程式將直接帶您到引發異常的代碼，並為您提供有用的錯誤訊息。

![發生序列化異常](../debugger/media/write-better-code-serialization-exception.png)

錯誤訊息指示不能將值`4o`解析為整數。 因此，在此示例中，您知道資料是壞的：`4o`應該是`40`。 但是，如果您在實際方案中無法控制資料（假設您是從 Web 服務獲取資料），您該怎麼辦？ 如何修復它？

當您遭遇異常時，您需要提出（並回答）幾個問題：

* 此異常是否只是您可以修復的 Bug？ 或者，

* 此異常是您的使用者可能會遇到的？

如果是前者，修復錯誤。 （在示例應用中，這意味著修復錯誤資料。如果是後者，您可能需要使用塊處理代碼中的異常（我們將在下一`try/catch`節中查看其他可能的策略）。 在示例應用中，替換以下代碼：

```csharp
users = ser.ReadObject(ms) as User[];
```

取代為此程式碼：

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

塊`try/catch`具有一些性能成本，因此您只想在真正需要它們時使用它們，即 （a） 它們可能發生在應用的發佈版本中，以及 （b） 方法的文檔指示您應該檢查異常（假設文檔已完成！ 在許多情況下，您可以適當地處理異常，使用者將永遠不會知道它。

以下是異常處理的幾個重要提示：

* 避免使用空 catch 塊（`catch (Exception) {}`如 ）不採取適當的操作來暴露或處理錯誤。 空或非資訊化 catch 塊可以隱藏異常，並使代碼更難調試，而不是更容易。

* 在示例`try/catch`應用中，使用引發異常的特定函數周圍的塊（`ReadObject`。 如果在較大的代碼塊周圍使用它，則最終會隱藏錯誤的位置。 例如，不要在調用父函數`try/catch``ReadToObject`（此處顯示）周圍使用塊，否則您無法確切知道異常發生的位置。

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* 對於應用中包含的不熟悉的函數，尤其是與外部資料（如 Web 請求）交互的函數，請查看文檔以查看該函數可能會引發哪些異常。 這對於正確處理錯誤和調試應用來說可能是關鍵資訊。

對於示例應用`SerializationException`，通過更改為`GetJsonData``4o``40`修復 方法中的 。

## <a name="clarify-your-code-intent-by-using-assert"></a>使用斷言闡明代碼意圖

按一下調試工具列 **（Ctrl** + **Shift** + **F5**） 中的**Restart**![重新開機應用](../debugger/media/dbg-tour-restart.png "重新開機應用")按鈕。 這將以更少的步驟重新開機應用。 您可以在主控台視窗中看到以下輸出。

![輸出中的空值](../debugger/media/write-better-code-using-assert-null-output.png)

您可以在此輸出中看到不太正確的內容。 **第**三條記錄的名稱和**姓氏**為空！

這是一個討論有用的編碼實踐的好時機，這種練習通常使用不足，即在函數中使用`assert`語句。 通過添加以下代碼，可以包含運行時檢查，以確保 和`firstname``lastname`不是`null`。 替換`UpdateRecords`方法中的以下代碼：

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

取代為這個：

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

通過在開發`assert`過程中向函數添加類似這樣的語句，可以説明指定代碼的意圖。 在前面的示例中，我們指定以下內容：

* 名字需要有效的字串
* 姓氏需要有效的字串

通過以這種方式指定意圖，可以強制實施您的要求。 這是一種簡單而方便的方法，可用於在開發過程中顯示 Bug。 （`assert`語句也用作單元測試中的主要元素。

按一下調試工具列 **（Ctrl** + **Shift** + **F5**） 中的**Restart**![重新開機應用](../debugger/media/dbg-tour-restart.png "重新開機應用")按鈕。

> [!NOTE]
> 代碼`assert`僅在調試生成中處於活動狀態。

重新開機時，調試器將`assert`暫停語句，因為運算式`users[i].firstname != null`將計算到`false`而不是`true`。

![斷言解析為 false](../debugger/media/write-better-code-using-assert.png)

該`assert`錯誤告訴您存在需要調查的問題。 `assert`可以涵蓋許多不一定看到異常的情況。 在此示例中，使用者不會看到異常，並且`null`將添加值，如`firstname`記錄清單中所示。 這可能會導致以後出現問題（如您在主控台輸出中看到的），並且可能更難調試。

> [!NOTE]
> 在調用`null`值上的方法的方案中，將生成`NullReferenceException`結果。 通常希望避免對常規異常（`try/catch`即未綁定到特定庫函數的異常）使用塊。 任何物件都可以引發`NullReferenceException`。 如果不確定，請查看庫功能的文檔。

在調試過程中，最好保留特定`assert`語句，直到您知道需要將其替換為實際的代碼修復程式。 假設您決定使用者在應用的發佈版本中可能會遇到異常。 在這種情況下，必須重構代碼，以確保你的應用不會引發致命異常或導致一些其他錯誤。 因此，要修復此代碼，請替換以下代碼：

```csharp
if (existingUser == false)
{
    User user = new User();
```

取代為此程式碼：

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

通過使用此代碼，您可以滿足代碼要求，並確保未將 具有`firstname`或`lastname``null`值的記錄添加到資料中。

在此示例中，我們在迴圈中添加了兩`assert`個語句。 通常，在使用`assert`時，最好在函數或`assert`方法的進入點（開頭）添加語句。 您當前正在查看示例應用中`UpdateRecords`的方法。 在此方法中，您知道如果任一方法參數是`null`，則請用函數進入點處的語句`assert`檢查它們。

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

對於前面的語句，您的意圖是載入現有資料 （`db`） 並在更新任何內容之前`users`檢索新資料 （ ）。

可以將解析為`assert``true`或`false`的任何類型的運算式一起使用。 因此，例如，您可以添加這樣的`assert`語句。

```csharp
Debug.Assert(users[0].points > 0);
```

如果要指定以下意圖，則上述代碼很有用：更新使用者記錄需要大於零 （0） 的新點值。

## <a name="inspect-your-code-in-the-debugger"></a>在調試器中檢查代碼

好了，現在你已經修復了示例應用出錯的所有關鍵內容，您可以轉到其他重要內容！

我們向您展示了調試器的異常協助程式，但調試器是一個更強大的工具，它還允許您執行其他操作，如步進代碼並檢查其變數。 這些更強大的功能在許多方案中非常有用，尤其是：

* 您正在嘗試在代碼中隔離運行時 Bug，但無法使用前面討論的方法和工具執行此操作。

* 您希望驗證代碼，即在代碼運行時監視它，以確保代碼按預期方式運行，並執行您期望的方式。

    在代碼運行時監視代碼是很有啟發性的。 您可以通過這種方式瞭解有關代碼的更多詳細資訊，並且通常可以在 Bug 出現任何明顯症狀之前識別它們。

要瞭解如何使用調試器的基本功能，請參閱[絕對初學者的調試](../debugger/debugging-absolute-beginners.md)。

## <a name="fix-performance-issues"></a>修正效能問題

另一種錯誤包括低效代碼，這些代碼會導致應用運行緩慢或使用過多的記憶體。 通常，優化性能是您在應用開發後期完成的事情。 但是，您可以儘早遇到性能問題（例如，您看到應用的某些部分運行緩慢），並且可能需要儘早流量分析工具測試應用。 有關分析工具（如 CPU 使用工具和記憶體分析器）的詳細資訊，請參閱[首先查看分析工具](../profiling/profiling-feature-tour.md)。

## <a name="next-steps"></a>後續步驟

在本文中，您已經瞭解如何避免和修復代碼中的許多常見錯誤以及何時使用調試器。 接下來，詳細瞭解如何使用 Visual Studio 調試器修復 Bug。

> [!div class="nextstepaction"]
> [適合完全初學者的偵錯](../debugger/debugging-absolute-beginners.md)
