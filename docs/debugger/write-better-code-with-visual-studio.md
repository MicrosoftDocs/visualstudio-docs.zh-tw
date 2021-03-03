---
title: 偵錯技術和工具
description: 使用 Visual Studio 修正例外狀況、修正錯誤，以及改善您的程式碼，以較少的 bug 撰寫更好的程式碼
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5fd3d8e17d90cde50f583dfc0393debf460de7f6
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684082"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>協助您撰寫更好的程式碼的偵錯工具技術和工具

修正您程式碼中的錯誤和錯誤可能會很耗時，有時也很令人沮喪--工作。 學習如何有效地進行調試需要一些時間，但強大的 IDE （例如 Visual Studio）可以讓您的工作變得更容易。 IDE 可協助您更快速地修正錯誤和偵錯工具代碼，而不只是這樣，但也可以協助您撰寫更好的程式碼，並減少錯誤。 本文的目的是要讓您全面瞭解「bug 修正」程式，讓您知道何時使用程式碼分析器、何時使用偵錯工具、如何修正例外狀況，以及如何編寫意圖的程式碼。 如果您已經知道需要使用偵錯工具，請參閱 [偵錯工具的第一次查看](../debugger/debugger-feature-tour.md)。

在本文中，我們將討論如何運用 IDE，讓您的程式碼撰寫會話更具生產力。 我們會討論數個工作，例如：

* 利用 IDE 的程式碼分析器準備程式碼進行偵錯工具

* 如何修正 (執行階段錯誤的例外狀況) 

* 如何使用 assert) 撰寫意圖 (程式碼，將 bug 最小化

* 使用偵錯工具的時機

為了示範這些工作，我們會顯示一些最常見的錯誤和 bug 類型，您會在嘗試對應用程式進行偵錯工具時遇到這些錯誤。 雖然範例程式碼是 c #，但概念資訊通常適用于 c + +、Visual Basic、JavaScript 和 Visual Studio 支援的其他語言 (但) 注明。 螢幕擷取畫面則使用 C# 表示。

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>建立範例應用程式，其中包含一些 bug 和錯誤

下列程式碼有一些您可以使用 Visual Studio IDE 修正的 bug。 這裡的應用程式是一個簡單的應用程式，可模擬從某個作業取得 JSON 資料、將資料還原序列化至物件，以及使用新的資料更新簡單的清單。

若要建立應用程式：

1. 您必須安裝 Visual Studio 並安裝 **.Net Core 跨平臺開發** 工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。

    如果您需要安裝工作負載，但已有 Visual Studio，請按一下 [**工具**  >  **取得工具及功能**]。 Visual Studio 安裝程式即會啟動。 選擇 [ **.Net Core 跨平臺開發** ] 工作負載，然後選擇 [ **修改**]。

1. 開啟 Visual Studio。

    ::: moniker range=">=vs-2019"
    在 [開始] 視窗中，選擇 [ **建立新專案**]。 在 [搜尋] 方塊中輸入 **主控台** ，然後選擇 [.net Core 的 **主控台應用程式** ]。 選擇 [下一步]。 輸入類似 **Console_Parse_JSON** 的專案名稱，然後按 **[下一步] 或 [** **建立**]，其中有任何可用的選項。

    若是 .NET Core，請選擇建議的目標架構 ( .NET Core 3.1) 或 .NET 5，然後選擇 [ **建立**]。

    如果您沒有看到適用于 .net Core 專案範本的 **主控台應用程式**，請移至 **工具** 的 [  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 選擇 [ **.Net Core 跨平臺開發** ] 工作負載，然後選擇 [ **修改**]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [ **新增專案** ] 對話方塊的左窗格中，選擇 [ **Visual c #**] 底下的 [ **主控台應用程式**]，然後在中間窗格中選擇 [ **主控台應用程式 ( .net Core)**]。 輸入類似 **Console_Parse_JSON** 的名稱，然後按一下 **[確定]**。

    如果您沒有看到 **主控台應用程式 ( .net Core)** 專案範本，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 選擇 [ **.Net Core 跨平臺開發** ] 工作負載，然後選擇 [ **修改**]。
    ::: moniker-end

    Visual Studio 隨即建立主控台專案，並出現在右窗格的 [方案總管] 中。

1. 將專案 *Program.cs* 檔中的預設程式碼取代為下列範例程式碼。

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

## <a name="find-the-red-and-green-squiggles"></a>找出 red 和綠波浪線！

在您嘗試啟動範例應用程式並執行偵錯工具之前，請先檢查程式碼編輯器中的程式碼，以取得紅色和綠色波浪線。 這些代表由 IDE 的程式碼分析器所識別的錯誤和警告。 Red 波浪線是編譯時期錯誤，您必須先修正這些錯誤，才能執行程式碼。 綠色波浪線是警告。 雖然您通常可以在不修正警告的情況下執行應用程式，但它們可能是錯誤的來源，而您通常會藉由調查它們來節省時間和問題。 如果您偏好使用清單視圖，這些警告和錯誤也會顯示在 [ **錯誤清單** ] 視窗中。

在範例應用程式中，您會看到幾個需要修正的紅色波浪線，以及一個您將查看的綠色。 以下是第一個錯誤。

![顯示為紅色波浪線的錯誤](../debugger/media/write-better-code-red-squiggle.png)

若要修正這個錯誤，您將查看 IDE 的另一項功能，以燈泡圖示表示。

## <a name="check-the-light-bulb"></a>檢查燈泡！

第一個紅色波浪線表示編譯時期錯誤。 將滑鼠停留在其上方，您會看到訊息 ```The name `Encoding` does not exist in the current context``` 。

請注意，這個錯誤會在左下方顯示燈泡圖示。 連同螺絲起子圖示 ![ 螺絲起子圖示 ](../ide/media/screwdriver-icon.png) ，燈泡圖示的燈泡圖示 ![ ](../ide/media/light-bulb-icon.png) 代表可協助您修正或重構程式碼內嵌的快速動作。 燈泡代表您 *應該* 修正的問題。 螺絲起子適用于您可能會選擇修正的問題。 使用第一個建議的修正程式來解決此錯誤，方法是按一下左邊的 [ **使用系統文字** ]。

![使用燈泡來修正程式碼](../debugger/media/write-better-code-missing-include.png)

當您按一下此專案時，Visual Studio 會 `using System.Text` 在 *Program.cs* 檔案的頂端新增語句，而紅色波浪線會消失。  (當您不確定建議的修正功能時，請選擇右邊的 [ **預覽變更** ] 連結，再套用修正。 ) 

上述錯誤通常是您在程式碼中加入新的語句來修正的常見錯誤 `using` 。 這種情況有幾個常見的類似錯誤，例如這 ```The type or namespace `Name` cannot be found.``` 類的錯誤可能表示遺漏元件參考 (以滑鼠右鍵按一下專案、選擇 [**加入**  >  **參考**]) 、拼錯的名稱，或您需要為 c # 新增 (的遺漏程式庫、以滑鼠右鍵按一下專案，然後選擇 [**管理 NuGet 套件**]) 。

## <a name="fix-the-remaining-errors-and-warnings"></a>修正剩餘的錯誤和警告

您可以在此程式碼中查看更多波浪線。 在這裡，您會看到常見的類型轉換錯誤。 當您將滑鼠停留在波浪線上時，您會看到程式碼嘗試將字串轉換為 int，除非您加入明確的程式碼以進行轉換，否則不支援此程式碼。

![類型轉換錯誤](../debugger/media/write-better-code-conversion-error.png)

由於程式碼分析器無法猜出您的意圖，因此沒有任何燈泡可協助您解決這種情況。 若要修正這個錯誤，您必須知道程式碼的意圖。 在此範例中，因為您嘗試加入，所以不太難看到 `points` 應該是數值 (整數) 值 `points` `totalpoints` 。

若要修正這個錯誤，請變更 `points` 類別的成員，如下所 `User` 示：

```csharp
[DataMember]
internal string points;
```

變更為以下程式碼：

```csharp
[DataMember]
internal int points;
```

程式碼編輯器中的紅色波浪線會消失。

接下來，將滑鼠停留在資料成員宣告中的綠色波浪線上方 `points` 。 程式碼分析器會告知您永遠不會指派值給變數。

![未指派變數的警告訊息](../debugger/media/write-better-code-warning-message.png)

通常，這代表需要修正的問題。 不過，在範例應用程式中，實際上是在還原序列化程式期間將資料儲存在 `points` 變數中，然後將該值加入至 `totalpoints` 資料成員。 在此範例中，您知道程式碼的意圖，並且可以安全地忽略警告。 但是，如果您想要排除警告，您可以取代下列程式碼：

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

當您修正所有的紅色波浪線並解決--或至少調查--所有綠色波浪線之後，您就可以開始偵錯工具並執行應用程式。

按 **F5** (**Debug > 開始調試**) **或啟動調試按鈕**![開始](../debugger/media/dbg-tour-start-debugging.png "[偵錯]")在調試工具列中進行調試。

此時，範例應用程式會擲回 `SerializationException` 例外狀況 () 的執行階段錯誤。 也就是，應用程式會在嘗試序列化的資料上進行淺淺化。 由於您已在偵錯工具中啟動應用程式 (偵錯工具已附加) ，偵錯工具的例外狀況協助程式會帶您前往擲回例外狀況的程式碼，並提供實用的錯誤訊息給您。

![發生 SerializationException](../debugger/media/write-better-code-serialization-exception.png)

錯誤訊息會指示您 `4o` 無法將該值剖析為整數。 因此，在此範例中，您知道資料不正確： `4o` 應為 `40` 。 但是，如果您無法控制真實案例中的資料 (假設您是從 web 服務) ，那麼您該怎麼做呢？ 如何修正此問題？

當您遇到例外狀況時，您需要詢問 (和回答) 幾個問題：

* 這個例外狀況是否只是您可以修正的 bug？ 或者，

* 這是您的使用者可能會遇到的例外狀況嗎？

如果是前者，請修正 bug。  (在範例應用程式中，這表示修正不正確的資料。 ) 如果是後者，您可能需要在程式碼中使用區塊處理例外狀況， `try/catch` (我們會在下一節中查看其他可能的策略) 。 在範例應用程式中，取代下列程式碼：

```csharp
users = ser.ReadObject(ms) as User[];
```

使用此程式碼取代：

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

`try/catch`區塊有一些效能成本，因此您只需要在真正需要時使用它們，也就是在應用程式的發行版本中 () ，以及 (b) 該方法的檔時，會指出您應該檢查例外狀況 (假設檔已完成！ ) 。 在許多情況下，您可以適當地處理例外狀況，而且使用者永遠不需要知道它的相關資訊。

以下是一些例外狀況處理的重要秘訣：

* 請避免使用空白的 catch 區塊，例如 `catch (Exception) {}` ，它不會採取適當的動作來公開或處理錯誤。 空白或不具資訊性的 catch 區塊可以隱藏例外狀況，而且可以讓您的程式碼更難進行偵錯工具，而不是更容易進行。

* `try/catch` `ReadObject` 在範例應用程式) 中，于擲回例外狀況 (的特定函式周圍使用區塊。 如果您在較大的程式碼區塊中使用它，您最後會隱藏錯誤的位置。 例如，請勿在父函式 `try/catch` 的呼叫周圍使用區塊 `ReadToObject` （如下所示），或者您不知道發生例外狀況的確切位置。

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

* 針對您在應用程式中包含的不熟悉函式，尤其是與外部資料 (（例如 web 要求) ）的互動，請查看檔，以查看函式可能會擲回的例外狀況。 這可能是適當的錯誤處理和對應用程式進行偵錯工具的重要資訊。

針對範例應用程式，請將 `SerializationException` 變更為，以修正方法中的 `GetJsonData` `4o` `40` 。

## <a name="clarify-your-code-intent-by-using-assert"></a>使用 assert 來表達您的程式碼意圖

按一下偵錯工具列中的 [**重新** 啟動 ![重新開機應用程式](../debugger/media/dbg-tour-restart.png ">restartapp")] 按鈕， (**Ctrl**  +  **Shift**  +  **F5**) 。 這會以較少的步驟重新開機應用程式。 您會在主控台視窗中看到下列輸出。

![輸出中的 Null 值](../debugger/media/write-better-code-using-assert-null-output.png)

您可以在此輸出中看到不太適合的內容。 第三筆記錄的 **名稱** 和 **lastname** 是空白的！

這是一個很好的時機，可以討論有説明的程式碼撰寫實務，通常是使用您函式 `assert` 中的語句。 藉由新增下列程式碼，您可以包含執行時間檢查，以確定 `firstname` 和 `lastname` 不是 `null` 。 取代方法中的下列程式碼 `UpdateRecords` ：

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

藉由在 `assert` 開發過程中將這類語句新增至您的函式，您可以協助指定程式碼的意圖。 在上述範例中，我們會指定下列各項：

* 第一個名稱需要有效的字串
* 姓氏必須有有效的字串

藉由以這種方式指定意圖，您將會強制執行您的需求。 這是簡單且便利的方法，可讓您在開發期間用來呈現 bug。  (`assert` 語句也用來作為單元測試中的主要元素。 ) 

按一下偵錯工具列中的 [**重新** 啟動 ![重新開機應用程式](../debugger/media/dbg-tour-restart.png ">restartapp")] 按鈕， (**Ctrl**  +  **Shift**  +  **F5**) 。

> [!NOTE]
> `assert`程式碼只在 Debug 組建中為作用中。

當您重新開機時，偵錯工具會在語句上暫停 `assert` ，因為運算式會 `users[i].firstname != null` 評估為， `false` 而不是 `true` 。

![Assert 解析為 false](../debugger/media/write-better-code-using-assert.png)

此 `assert` 錯誤指出您需要調查的問題。 `assert` 可以涵蓋許多您不一定會看到例外狀況的案例。 在此範例中，使用者不會看到例外狀況，而且會 `null` `firstname` 在您的記錄清單中新增一個值。 這可能會在 (，例如您在主控台輸出中看到) ，而且可能較難進行調試。

> [!NOTE]
> 在您于值上呼叫方法的情況下 `null` ，會 `NullReferenceException` 產生結果。 您通常會想要避免使用 `try/catch` 一般例外狀況的區塊，也就是未系結至特定程式庫函數的例外狀況。 任何物件都可以擲回 `NullReferenceException` 。 如果您不確定，請檢查程式庫函數的檔。

在進行偵錯工具時，最好先保留特定的 `assert` 語句，直到您知道需要將它取代為實際的程式碼修正。 假設您決定使用者可能會在應用程式的發行組建中遇到例外狀況。 在這種情況下，您必須重構程式碼，以確定您的應用程式不會擲回嚴重的例外狀況，或導致其他錯誤。 因此，若要修正此程式碼，請取代下列程式碼：

```csharp
if (existingUser == false)
{
    User user = new User();
```

使用此程式碼取代：

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

藉由使用此程式碼，您就可以滿足您的程式碼需求，並確保資料中的 `firstname` 或 `lastname` 值的記錄 `null` 不會加入至資料。

在此範例中，我們已在 `assert` 迴圈內新增兩個語句。 一般來說，在使用時， `assert` 最好 `assert` 在進入點加入語句， (開始) 函數或方法。 您目前正在查看 `UpdateRecords` 範例應用程式中的方法。 在這個方法中，如果其中一個方法引數是，您就會知道有問題 `null` ，因此請使用函式進入點的語句來檢查它們 `assert` 。

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

針對上述的語句，您的目的是要將現有的資料 (`db`) ，然後在更新任何資料之前， () 取得新 `users` 的資料。

您可以搭配 `assert` 解析為或的任何類型運算式使用 `true` `false` 。 例如，您可以加入 `assert` 如下的語句。

```csharp
Debug.Assert(users[0].points > 0);
```

如果您想要指定下列意圖，上述程式碼會很有用：若要更新使用者的記錄，則必須有大於零的新點值 (0) 。

## <a name="inspect-your-code-in-the-debugger"></a>在偵錯工具中檢查您的程式碼

好的，現在您已修正範例應用程式中的所有重大問題，您可以移至其他重要的內容！

我們向您示範偵錯工具的例外狀況協助程式，但偵錯工具是更強大的工具，也可讓您執行其他動作，例如逐步執行程式碼及檢查其變數。 這些功能更強大的功能在許多情況下都很有用，尤其是：

* 您正在嘗試隔離程式碼中的執行時間 bug，但無法使用先前討論的方法和工具來進行。

* 您想要驗證您的程式碼，也就是在執行時監看它，以確保它會以您預期的方式運作，並執行您想要的動作。

    在程式碼執行時監看您的程式碼是有意義的。 您可以透過這種方式進一步瞭解您的程式碼，而且通常可以在資訊清單出現任何明顯的徵兆之前識別出 bug。

若要瞭解如何使用偵錯工具的基本功能，請參閱 [絕對初學者的調試](../debugger/debugging-absolute-beginners.md)程式。

## <a name="fix-performance-issues"></a>修正效能問題

另一種情況的錯誤包括效率不佳的程式碼，導致您的應用程式執行速度變慢或使用過多的記憶體。 一般來說，將效能優化是您稍後在應用程式開發中執行的一些作業。 不過，您可以提早遇到效能問題 (例如，您會看到應用程式的某些部分執行速度很慢) ，而您可能需要提早流量分析工具測試您的應用程式。 如需分析工具的詳細資訊（例如 CPU 使用量工具和記憶體分析器），請參閱程式碼 [剖析工具的第一看](../profiling/profiling-feature-tour.md)。

## <a name="next-steps"></a>下一步

在本文中，您已瞭解如何避免和修正程式碼中的許多常見錯誤，以及使用偵錯工具的時機。 接下來，請深入瞭解如何使用 Visual Studio 偵錯工具來修正 bug。

> [!div class="nextstepaction"]
> [適合完全初學者的偵錯](../debugger/debugging-absolute-beginners.md)
