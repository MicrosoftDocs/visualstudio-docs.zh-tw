---
title: 偵錯技術和工具
description: 使用 Visual Studio 修正例外狀況、修正錯誤，並改善您的程式碼，以較少的 bug 撰寫較佳的程式碼
ms.custom:
- debug-experiment
- seodec18
ms.date: 01/24/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1fe0a9bb1e966bd1451bb5d816eaab814071fb5
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000171"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>可協助您撰寫更好的程式碼的偵錯工具技術和工具

修正程式碼中的錯誤和錯誤可能會很耗時，而且有時候會令人沮喪--工作。 需要時間學習如何有效地進行調試，但功能強大的 IDE （例如 Visual Studio）可以讓您的工作變得更容易。 IDE 可協助您更快速地修正錯誤和對程式碼的偵錯工具，而不只是這麼做，還可協助您以較少的錯誤來撰寫更好的程式碼。 本文旨在提供「bug 修正」程式的整體觀點，讓您知道何時使用程式碼分析器、何時使用偵錯工具、如何修正例外狀況，以及如何撰寫意圖的程式碼。 如果您已經知道需要使用偵錯工具，請參閱[偵錯工具的第一次](../debugger/debugger-feature-tour.md)查看。

在本文中，我們會討論如何利用 IDE 讓您的編碼會話更具生產力。 我們會接觸數項工作，例如：

* 利用 IDE 的程式碼分析器來準備您的程式碼以進行偵錯工具

* 如何修正例外狀況（執行階段錯誤）

* 如何藉由撰寫意圖的程式碼來將 bug 降至最低（使用 assert）

* 使用偵錯工具的時機

為了示範這些工作，我們會示範幾個最常見的錯誤和 bug 的類型，您會在嘗試對應用程式進行 debug 時遇到。 雖然範例程式碼是C#，但概念資訊通常適用于C++、Visual Basic、JavaScript 和 Visual Studio 支援的其他語言（除非另有注明）。 螢幕擷取畫面則使用 C# 表示。

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>建立範例應用程式，其中包含一些 bug 和錯誤

下列程式碼有一些 bug，您可以使用 Visual Studio IDE 加以修正。 這裡的應用程式是一個簡單的應用程式，可模擬從某個作業取得 JSON 資料、將資料還原序列化為物件，以及使用新的資料更新簡單的清單。

建立應用程式：

1. 開啟 Visual Studio，然後**選擇 [** 檔案 > **新增** > **專案**]。 在 **[ C#視覺效果**] 底下，選擇 [ **Windows 桌面**] 或 [ **.net Core**]，然後在中間窗格中選擇**主控台應用程式**。

    > [!NOTE]
    > 如果您沒有看到 [主控台應用程式] 專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio 安裝程式即會啟動。 選擇 [.NET 桌面開發] (或 [.NET Core 跨平台開發]) 工作負載，然後選擇 [修改]。

2. 在 [**名稱**] 欄位中，輸入**Console_Parse_JSON** ，然後按一下 **[確定]** 。 Visual Studio 會建立專案。

3. 將專案的*Program.cs*檔中的預設程式碼取代為下列範例程式碼。

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

## <a name="find-the-red-and-green-squiggles"></a>找出紅色和綠色的波浪線！

在您嘗試啟動範例應用程式並執行偵錯工具之前，請先查看 [程式碼編輯器] 中的程式碼是否有紅色和綠色波浪線。 這些代表由 IDE 的程式碼分析器所識別的錯誤和警告。 紅色波浪線是編譯時期錯誤，您必須先修正這些錯誤，才能執行程式碼。 綠色波浪線是警告。 雖然您通常可以在不修正警告的情況下執行應用程式，但它們可能是 bug 的來源，而且您通常會藉由調查來節省時間和問題。 如果您偏好使用清單視圖，則這些警告和錯誤也會顯示在 [**錯誤清單**] 視窗中。

在範例應用程式中，您會看到需要修正的幾個紅色波浪線，以及您要查看的一個綠色。 以下是第一個錯誤。

![顯示為紅色波浪線的錯誤](../debugger/media/write-better-code-red-squiggle.png)

若要修正此錯誤，您將查看 IDE 的另一個功能，以燈泡圖示表示。

## <a name="check-the-light-bulb"></a>檢查燈泡！

第一個紅色波浪線代表編譯時期錯誤。 將滑鼠停留在其上方，您就會看到 ```The name `Encoding` does not exist in the current context```的訊息。

請注意，此錯誤顯示左下方的燈泡圖示。 除了螺絲起子圖示 ![螺絲起子圖示](../ide/media/screwdriver-icon.png)，燈泡圖示 ![燈泡圖示](../ide/media/light-bulb-icon.png) 代表可協助您修正或重構程式碼內嵌的快速動作。 燈泡代表您*應該*修正的問題。 螺絲起子適用于您可能選擇修正的問題。 使用第一個建議的修正程式，按一下左側的 [**使用系統**] 解決此錯誤。

![使用燈泡來修正程式碼](../debugger/media/write-better-code-missing-include.png)

當您按一下此專案時，Visual Studio 會在*Program.cs*檔案頂端加入 `using System.Text` 語句，紅色的波浪線就會消失。 （如果您不確定建議的修正程式，請選擇右側的 [**預覽變更**] 連結，然後再套用修正程式）。

先前的錯誤是通常會藉由將新的 `using` 語句加入至程式碼來修正的常見錯誤。 這個問題有數個常見的類似錯誤，例如 ```The type or namespace `Name` cannot be found.``` 這類錯誤可能表示遺漏元件參考（以滑鼠右鍵按一下專案、選擇 [**加入** > **參考**]）、拼錯的名稱，或您需要新增的遺漏程式庫（針對，以C#滑鼠右鍵按一下專案，然後選擇 [**管理 NuGet 封裝**]）。

## <a name="fix-the-remaining-errors-and-warnings"></a>修正其餘的錯誤和警告

還有幾個波浪線可以在此程式碼中查看。 在這裡，您會看到一般類型轉換錯誤。 當您將滑鼠停留在波浪線上方時，您會看到程式碼正嘗試將字串轉換成 int，除非您加入明確的程式碼來進行轉換，否則不支援這種情況。

![類型轉換錯誤](../debugger/media/write-better-code-conversion-error.png)

由於程式碼分析器無法猜出您的意圖，因此不會有任何燈泡可協助您進行這次。 若要修正此錯誤，您必須知道程式碼的意圖。 在此範例中，因為您嘗試將 `points` 加入 `totalpoints`，所以不太難看到 `points` 應該是數值（整數）值。

若要修正這個錯誤，請變更 `User` 類別的 `points` 成員，如下所示：

```csharp
[DataMember]
internal string points;
```

轉換為：

```csharp
[DataMember]
internal int points;
```

程式碼編輯器中的紅色波浪線會消失。

接下來，將滑鼠停留在 `points` 資料成員的宣告中的綠色波浪線上。 程式碼分析器會告訴您，變數從未被指派值。

![未指派變數的警告訊息](../debugger/media/write-better-code-warning-message.png)

一般而言，這代表需要修正的問題。 不過，在範例應用程式中，您實際上是在還原序列化程式期間將資料儲存在 `points` 變數中，然後將該值加入 `totalpoints` 資料成員中。 在此範例中，您知道程式碼的意圖，並且可以安全地忽略此警告。 不過，如果您想要消除警告，可以取代下列程式碼：

```csharp
item.totalpoints = users[i].points;
```

取代為這個：

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

綠色波浪線會消失。

## <a name="fix-an-exception"></a>修正例外狀況

當您已修正所有 red 波浪線和已解決--或至少已調查--所有綠色波浪線時，您已準備好啟動偵錯工具並執行應用程式。

按下 **F5** ([偵錯] > [開始偵錯]) 或在偵錯工具列中按下 [開始偵錯] 按鈕 ![開始偵錯](../debugger/media/dbg-tour-start-debugging.png "開始偵錯")。

此時，範例應用程式會擲回 `SerializationException` 例外狀況（執行階段錯誤）。 也就是說，應用程式會在嘗試序列化的資料上以淺的方式來進行。 由於您是在 debug 模式中啟動應用程式（已附加偵錯工具），因此偵錯工具的例外狀況 Helper 會直接帶您前往擲回例外狀況的程式碼，並提供有用的錯誤訊息。

![發生 SerializationException](../debugger/media/write-better-code-serialization-exception.png)

錯誤訊息會指示您 `4o` 的值無法剖析為整數。 因此，在此範例中，您知道資料不正確：應該 `40``4o`。 不過，如果您不能控制實際案例中的資料（假設您是從 web 服務取得），那麼您該怎麼做呢？ 如何修正此問題？

當您遇到例外狀況時，您需要詢問（並回答）幾個問題：

* 這個例外狀況只是您可以修正的 bug 嗎？ 或者，

* 這是您的使用者可能會遇到的例外狀況嗎？

如果是前者，請修正 bug。 （在範例應用程式中，這表示會修正錯誤的資料）。如果是後者，您可能需要使用 `try/catch` 區塊來處理常式代碼中的例外狀況（我們會在下一節中探討其他可能的策略）。 在範例應用程式中，取代下列程式碼：

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

`try/catch` 區塊有一些效能成本，因此您只會在需要時才使用它們，也就是在應用程式的發行版本中可能發生的情況，以及（b）方法的檔指出您應該檢查是否有例外狀況（假設檔已完成！）。 在許多情況下，您可以適當地處理例外狀況，而使用者也不需要知道它。

以下是例外狀況處理的幾個重要秘訣：

* 請避免使用空的 catch 區塊，例如 `catch (Exception) {}`，這不會採取適當的動作來公開或處理錯誤。 空白或不具資訊性的 catch 區塊可以隱藏例外狀況，而且可能會讓您的程式碼更容易進行 debug，而不是更輕鬆。

* 針對在範例應用程式中擲回例外狀況（`ReadObject`的特定函式，請使用 `try/catch` 區塊。 如果您在較大的程式碼區塊周圍使用它，最後會隱藏錯誤的位置。 例如，請勿在呼叫父函式 `ReadToObject`時使用 `try/catch` 區塊，如下所示，否則您不會知道發生例外狀況的確切位置。

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

* 針對您在應用程式中包含的不熟悉函式，特別是與外部資料互動的函式（例如 web 要求），請參閱檔，以查看函式可能會擲回的例外狀況。 這可能是適當的錯誤處理和用於偵測應用程式的重要資訊。

針對範例應用程式，將 `4o` 變更為 `40`，以修正 `GetJsonData` 方法中的 `SerializationException`。

## <a name="clarify-your-code-intent-by-using-assert"></a>使用 assert 來闡明您的程式碼意圖

按一下偵錯工具列中的 [重新啟動] ![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp") 按鈕 (**Ctrl** + **Shift** + **F5**)。 這會以較少的步驟重新開機應用程式。 您會在主控台視窗中看到下列輸出。

![輸出中的 Null 值](../debugger/media/write-better-code-using-assert-null-output.png)

您可以在此輸出中看到不是正確的東西。 第三筆記錄的**name**和**lastname**是空白的！

這是一個很好的時機，可以說是一種很有用的編碼做法，也就是在函式中使用 `assert` 語句。 藉由新增下列程式碼，您可以加入執行時間檢查，以確保不會 `null``firstname` 和 `lastname`。 取代 `UpdateRecords` 方法中的下列程式碼：

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

藉由在開發過程中，將像這樣的 `assert` 語句加入至您的函式，您可以協助指定程式碼的意圖。 在上述範例中，我們會指定下列各項：

* 第一個名稱需要有效的字串
* 姓氏需要有效的字串

藉由以這種方式指定意圖，您可以強制執行您的需求。 這是一種簡單又方便的方法，可讓您在開發期間用來呈現 bug。 （`assert` 語句也用來做為單元測試中的主要元素）。

按一下偵錯工具列中的 [重新啟動] ![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp") 按鈕 (**Ctrl** + **Shift** + **F5**)。

> [!NOTE]
> `assert` 程式碼只在 Debug 組建中為作用中。

當您重新開機時，偵錯工具會在 `assert` 語句上暫停，因為運算式 `users[i].firstname != null` 會評估為 `false`，而不是 `true`。

![Assert 解析為 false](../debugger/media/write-better-code-using-assert.png)

`assert` 錯誤指出您需要調查的問題。 `assert` 可以涵蓋許多您不一定會看到例外狀況的案例。 在此範例中，使用者不會看到例外狀況，而且會在您的記錄清單中加入 `firstname` 的 `null` 值。 這可能會在稍後造成問題（例如您在主控台輸出中看到），而且可能會比較難進行調試。

> [!NOTE]
> 在您呼叫 `null` 值上之方法的案例中，`NullReferenceException` 的結果。 您通常會想要避免使用 `try/catch` 區塊進行一般例外狀況，也就是未系結至特定程式庫函式的例外狀況。 任何物件都可以擲回 `NullReferenceException`。 如果您不確定，請參閱程式庫函式的檔。

在進行偵錯工具的過程中，保留特定的 `assert` 語句是很好的，直到您知道需要以實際的程式碼修正來取代它為止。 假設您決定使用者可能會在應用程式的發行組建中遇到例外狀況。 在這種情況下，您必須重構程式碼，以確保您的應用程式不會擲回嚴重例外狀況，或導致其他錯誤。 因此，若要修正此程式碼，請取代下列程式碼：

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

藉由使用此程式碼，您可以滿足您的程式碼需求，並確定具有 `firstname` 或 `lastname` 值 `null` 的記錄不會加入至資料中。

在此範例中，我們在迴圈內新增了兩個 `assert` 語句。 一般來說，使用 `assert`時，最好是在函式或方法的進入點（開頭）新增 `assert` 語句。 您目前正在查看範例應用程式中的 `UpdateRecords` 方法。 在此方法中，如果其中一個方法引數 `null`，您就會知道您有問題，因此請在函式的進入點使用 `assert` 語句來檢查它們。

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

針對上述語句，您的目的是要載入現有的資料（`db`）並抓取新的資料（`users`），然後再更新任何專案。

您可以使用 `assert` 搭配任何類型的運算式，以解析成 `true` 或 `false`。 例如，您可以加入 `assert` 語句，如下所示。

```csharp
Debug.Assert(users[0].points > 0);
```

如果您想要指定下列意圖，上述程式碼就很有用：必須有大於零（0）的新點值，才能更新使用者的記錄。

## <a name="inspect-your-code-in-the-debugger"></a>在偵錯工具中檢查程式碼

好的，現在您已修正範例應用程式中所有錯誤的關鍵，您可以移至其他重要的東西！

我們向您示範了偵錯工具的例外狀況協助程式，但偵錯工具是一個功能更強大的工具，可讓您執行其他動作，例如逐步執行程式碼並檢查其變數。 這些更強大的功能在許多情況下都很有用，特別是下列各項：

* 您嘗試在程式碼中隔離執行時間 bug，但無法使用先前所討論的方法和工具來執行。

* 您想要驗證您的程式碼，也就是在執行時監看它，以確保它會以您預期的方式運作，並執行您想要的動作。

    當您的程式碼執行時，它會有意義地進行監看。 您可以透過這種方式深入瞭解程式碼，而且通常可以在錯誤列出任何明顯的徵兆之前識別 bug。

若要瞭解如何使用偵錯工具的基本功能，請參閱[適用于絕對初學者的調試](../debugger/debugging-absolute-beginners.md)程式。

## <a name="fix-performance-issues"></a>修正效能問題

另一種類型的錯誤包括讓應用程式執行速度變慢或使用太多記憶體的效率不佳的程式碼。 一般來說，將效能優化是您稍後在應用程式開發時所做的事。 不過，您可以提早遇到效能問題（例如，您看到應用程式的某些部分執行速度緩慢），而且您可能需要及早流量分析工具來測試應用程式。 如需分析工具（例如 CPU 使用量工具和記憶體分析器）的詳細資訊，請參閱程式碼[剖析工具的第一次](../profiling/profiling-feature-tour.md)查看。

## <a name="next-steps"></a>後續步驟

在本文中，您已瞭解如何避免及修正程式碼中的許多常見 bug，以及使用偵錯工具的時機。 接下來，深入瞭解如何使用 Visual Studio 偵錯工具來修正 bug。

> [!div class="nextstepaction"]
> [適合完全初學者的偵錯](../debugger/debugging-absolute-beginners.md)
