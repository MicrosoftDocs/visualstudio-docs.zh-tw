---
title: 可讓您撰寫的 Visual Studio 說明C#程式碼較少的 bug
description: 了解如何撰寫更好的程式碼較少的 bug
ms.custom: debug-experiments
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4cf3c7ae8b45f6d3410925977c2c67784b1ca6d
ms.sourcegitcommit: a811f6a194ccd40d844e74e618d847df87c85c16
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2018
ms.locfileid: "52621587"
---
# <a name="fix-bugs-by-writing-better-c-code-using-visual-studio"></a>藉由撰寫更好修正 bugC#使用 Visual Studio 程式碼

偵錯程式碼時，可能很耗時-，而且有時候挫折-工作。 需要一段時間，以了解如何有效地偵錯，但功能強大的 IDE，例如 Visual Studio 可讓您的工作輕鬆許多。 IDE 可協助您更快速地偵錯您的程式碼並不只是的但它也可以幫助您撰寫更好的程式碼且錯誤更少。 我們在本文中的目標是為您提供的偵錯的程序的整體檢視，讓您將了解何時使用程式碼分析工具，以使用偵錯工具，以及何時使用其他工具時。  

在本文中，我們會討論利用 IDE，可讓您偵錯工作階段更具生產力。 我們介紹數個工作，例如：

* 準備您的程式碼進行偵錯利用 IDE 的程式碼分析工具

* 如何修正例外狀況 （執行階段錯誤）

* 如何撰寫程式碼的意圖，以減少錯誤

* 使用偵錯工具的時機

為了示範這些工作，我們會示範幾個最常見的錯誤和嘗試偵錯您的應用程式時，將會遇到的錯誤類型。 雖然程式碼範例C#，提供的概念性資訊是廣泛適用於 c + +、 Visual Basic、 JavaScript、 Visual Studio 其他語言支援 （除了註明）。 螢幕擷取畫面則使用 C# 表示。

## <a name="follow-along-using-the-sample-app"></a>遵循指示使用範例應用程式

如果您想，您可以建立包含確切的 bug 的.NET Framework 或.NET Core 主控台應用程式和我們在這裡所說明，而且您可以跟著做，並自行修正的錯誤。

若要建立應用程式，請開啟 Visual Studio 並選擇**檔案 > 新增專案**。 底下**Visual C#** ，選擇**Windows 桌面**或是 **.NET Core**，然後在中間窗格選擇**主控台應用程式**。 輸入名稱，例如**Console_Parse_JSON**然後按一下**確定**。 Visual Studio 會建立專案。 貼上[程式碼範例](#sample-code)到專案的*Program.cs*檔案。

> [!NOTE]
> 如果您沒有看到 [主控台應用程式] 專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio 安裝程式即會啟動。 選擇 [.NET 桌面開發] (或 [.NET Core 跨平台開發]) 工作負載，然後選擇 [修改]。

## <a name="find-the-red-and-green-squiggles"></a>尋找紅色和綠色波浪線 ！

您嘗試啟動範例應用程式，並執行偵錯工具之前，請檢查紅色和綠色波浪線的程式碼編輯器中的程式碼。 這些代表錯誤和 IDE 的程式碼分析器所識別的警告。 紅色波浪線會產生編譯時期錯誤，您必須修正之前的可執行程式碼。 綠色波浪線會是警告。 雖然您通常可以執行您的應用程式，而不修正警告，它們可以是錯誤的來源，您通常自己節省時間和麻煩調查它們。 這些警告和錯誤也顯示在**錯誤清單** 視窗中，如果您偏好的清單檢視。

在範例應用程式中，您會看到數個紅色的波浪線，您必須修正，以及一個綠色將探討。 以下是第一個錯誤。

![錯誤顯示為紅色的波浪線](../debugger/media/write-better-code-red-squiggle.png)

若要修正這個錯誤，您將探討的 IDE 中，燈泡圖示所代表的另一項功能。

## <a name="check-the-light-bulb"></a>請檢查燈泡 ！

第一個紅色的波浪線代表編譯時期錯誤。 將滑鼠停留，而且您看到訊息```The name `Encoding` does not exist in the current context```。

請注意，此錯誤會顯示較低的左邊的燈泡圖示。 以及它的螺絲起子圖示![螺絲起子圖示](../ide/media/screwdriver-icon.png)，燈泡圖示![燈泡圖示](../ide/media/light-bulb-icon.png)代表快速動作可協助您修正或重構程式碼內嵌。 燈泡代表問題*應該*修正。 螺絲起子適用於您可能會選擇修正的問題。 若要解決這個錯誤，請按一下 使用第一個建議的修正**使用 System.Text**左側。

![您可以使用燈泡來修正程式碼](../debugger/media/write-better-code-missing-include.png)

當您按一下此項目時，Visual Studio 會加入`using System.Text`陳述式，在頂端*Program.cs*檔案和紅色波浪線就會消失。 (當您不確定建議的修正程式會執行什麼動作時，選擇**預覽變更**之前套用修正程式右邊的連結。)

先前的錯誤是常見，通常是藉由新增新的修正`using`陳述式，以您的程式碼。 有數種錯誤常見，類似這個的這類```The type or namespace `Name` cannot be found.```這種錯誤可能表示遺漏的組件參考 (以滑鼠右鍵按一下專案，選擇**新增** > **參考**)，名稱拼錯或您要使用 NuGet 新增遺漏程式庫 (以滑鼠右鍵按一下專案，然後選擇 **管理 NuGet 套件**)。

## <a name="fix-the-errors-and-warnings"></a>修正的錯誤和警告

有幾個的多個波浪線，查看在這個程式碼。 在這裡，您會看到常見的類型轉換錯誤。 當您停留在波浪線上時，您會看到程式碼嘗試將字串轉換成整數，但並不支援，除非您將新增明確的程式碼来進行轉換。

![類型轉換錯誤](../debugger/media/write-better-code-conversion-error.png)

由於程式碼分析工具無法猜出您的目的，會有可協助您目前沒有燈泡。 若要修正這個錯誤，您需要知道的程式碼意圖。 在此範例中，不難發現`points`應該是數字 （整數） 值，因為您嘗試新增`points`至`totalpoints`。

若要修正這個錯誤，變更`points`隸屬`User`從這個類別：

```csharp
[DataMember]
internal string points;
```

轉換為：

```csharp
[DataMember]
internal int points;
```

程式碼編輯器中的紅色曲線已消失。

接下來，將滑鼠游標停留在宣告中的彎曲的綠色`points`資料成員。 程式碼分析工具會告訴您永遠不會指派給變數的值。

![指派變數的警告訊息](../debugger/media/write-better-code-warning-message.png)

一般而言，這表示需要修正的問題。 不過，範例應用程式實際上資料存放在`points`期間還原序列化程序中，並再將該值新增至變數`totalpoints`資料成員。 在此範例中，您需要知道的程式碼意圖並可以放心地忽略此警告。 不過，如果您想要排除警告，您可以取代下列程式碼：

```csharp
item.totalpoints = users[i].points;
```

取代為這個：

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

綠色波浪線就會消失。

## <a name="fix-an-exception"></a>修正例外狀況

當您已修正所有紅色的波浪線和解決，或至少調查-所有綠色波浪線，您已準備好開始偵錯工具，並執行應用程式。

按下 **F5** ([偵錯] > [開始偵錯]) 或在偵錯工具列中按下 [開始偵錯] 按鈕 ![開始偵錯](../debugger/media/dbg-tour-start-debugging.png "開始偵錯")。

到目前為止，範例應用程式會擲回`SerializationException`例外狀況 （執行階段錯誤）。 也就是您應用程式可以在它嘗試要序列化的資料。 因為您在偵錯模式 （附加偵錯工具） 中啟動應用程式，則偵錯工具的例外狀況協助程式會帶您前往擲回例外狀況，並提供您很有幫助的錯誤訊息的程式碼的權限。

![SerializationException，就會發生](../debugger/media/write-better-code-serialization-exception.png)

錯誤訊息指示您的值`4o`無法剖析為整數。 因此，在此範例中，您知道的資料不正確：`4o`應該是`40`。 不過，如果您未控制的資料在真實案例 （例如您從 web 服務取得它），怎麼一下嗎？ 您要如何修正此？

當您叫用例外狀況時，您需要要求 （及回答） 幾個問題：

* 是這個例外狀況就可以修正的 bug？ 或者，

* 您的使用者可能會遇到的項目是這個例外狀況？

如果是前者，修正 bug。 （在範例應用程式中，這表示修正不正確的資料。）如果是後者，您可能需要處理的例外狀況，在程式碼中使用`try/catch`區塊 （我們看看其他可能的修正下, 一節）。 在範例應用程式中，將下列程式碼：

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

A`try/catch`區塊有一些效能成本，因此您只會想要使用它們時您真的需要它們，也就是其中 (a) 可能會發生在應用程式的發行版本，以及 (b) 文件的方法可讓您表示您應該檢查（假設文件已完成 ！） 的例外狀況。 在許多情況下，可以適當地處理例外狀況，使用者將永遠不需要了解它。

以下是幾個例外狀況處理的重要秘訣：

* 避免使用空的 catch 區塊中，例如`catch (Exception) {}`，未採用適當的動作來公開 （expose） 或處理錯誤。 空的或非參考的 catch 區塊可以隱藏例外狀況，而且可以讓您的程式碼更難進行偵錯，而不是更容易。

* 使用`try/catch`擲回例外狀況的特定函式的區塊 (`ReadObject`，範例應用程式中)。 如果您使用較大的程式碼區塊前後，您會得到隱藏錯誤的位置。 比方說，不用`try/catch`父函式呼叫周圍區塊`ReadToObject`，這裡顯示，或您不知道確實發生例外狀況。

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

* 對於您在您的應用程式，expecially 中包含這些外部資料 （例如 web 要求） 互動的熟悉函式，檢查以查看哪些例外狀況的函式是可能會擲回的文件。 這可能是適當的錯誤處理和偵錯您的應用程式的重要資訊。

範例應用程式中，修正`SerializationException`中`GetJsonData`方法，藉由變更`4o`至`40`。

## <a name="clarify-your-code-intent-by-using-assert"></a>釐清您的程式碼的目的，使用判斷提示

按一下偵錯工具列中的 [重新啟動] ![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp") 按鈕 (**Ctrl** + **Shift** + **F5**)。 這會應用程式更少的步驟重新啟動。 您會看到下列輸出在主控台視窗中。

![在輸出中的 null 值](../debugger/media/write-better-code-using-assert-null-output.png)

您可以看到不對此輸出中的項目。 **名稱**並**lastname**第三個記錄為空白 ！

這是就是使用很有幫助的程式撰寫作法，通常很低，所討論的好時機`assert`中您的函式的陳述式。 您可以藉由新增下列程式碼，包含執行階段檢查，以確保能夠`firstname`並`lastname`不是`null`。 取代下列程式碼中的`UpdateRecords`方法：

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

藉由新增`assert`陳述式，這類以您的函式在開發程序，您可以協助將您的程式碼的意圖指定。 在上述範例中，我們指定下列項目：

* 有效的字串是第一個名稱為必要
* 有效的字串是為了姓氏

藉由指定意圖，如此一來，您將強制執行您的需求。 這是簡單且方便的方法，您可以在開發期間使用介面的錯誤。 (`assert`陳述式也可作為單元測試中的主要項目。)

按一下偵錯工具列中的 [重新啟動] ![重新啟動應用程式](../debugger/media/dbg-tour-restart.png "RestartApp") 按鈕 (**Ctrl** + **Shift** + **F5**)。

> [!NOTE]
> `assert`程式碼是只有在偵錯組建。

當您重新啟動時，偵錯工具暫停上`assert`陳述式，因為運算式`users[i].firstname != null`評估為`false`而不是`true`。

![判斷提示會解析為 false](../debugger/media/write-better-code-using-assert.png)

`assert`錯誤告訴您，是您要調查的問題。 `assert` 可以涵蓋許多的案例不一定了例外狀況。 在此範例中，使用者不會看到例外狀況，以及`null`以加入值，取得`firstname`在清單中的記錄。 這可能會造成問題更新版本上 （例如，您會看到主控台輸出中），而且可能很難偵錯。

> [!NOTE]
> 在呼叫方法的情況下`null`值，`NullReferenceException`結果。 您通常想要避免使用`try/catch`封鎖一般的例外狀況，也就是不受限於特定的程式庫函式的例外狀況。 任何物件可能會擲回`NullReferenceException`。 如果您不確定，請檢查程式庫函式的文件。

在偵錯過程中，最好保留特定`assert`陳述式，直到您知道您需要將它取代實際的程式碼修正。 例如，假設您決定使用者可能會遇到應用程式的發行組建中的例外狀況。 在此情況下，您必須重構程式碼，以確定您的應用程式不會擲回嚴重的例外狀況或一些其他錯誤所導致。 因此，若要修正此程式碼，取代下列程式碼：

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

使用此程式碼，來滿足您的程式碼的需求，並確定具有的資料錄`firstname`或`lastname`的值`null`不會加入至資料。

在此範例中，我們會新增兩個`assert`迴圈內的陳述式。 一般而言，使用時`assert`，所以最好先新增`assert`陳述式的函式或方法的進入點 （開始）。 您目前正在查看`UpdateRecords`範例應用程式中的方法。 在此方法中，您知道是否任何一種方法的引數是麻煩`null`，因此請查看這兩者同時使用`assert`函式的進入點的陳述式。

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

如先前的陳述式中，您的目的是您將現有的資料 (`db`)，並擷取新的資料 (`users`) 更新的任何項目之前。

您可以使用`assert`處理任何種類的運算式，會解析成`true`或`false`。 因此，比方說，您可以新增`assert`如下的陳述式。

```csharp
Debug.Assert(users[0].points > 0);
```

上述程式碼是很有用，如果您想要指定下列的意圖： 新的點值大於零 (0)，才能更新使用者的記錄。

## <a name="inspect-your-code-in-the-debugger"></a>檢查您的程式碼偵錯工具

好，既然您已修正問題的範例應用程式的所有重要，您可以移動到其他重要的東西 ！

我們剛才偵錯工具的例外狀況協助程式，但偵錯工具是一種功能更強大的工具，也可讓您進行其他動作，例如逐步執行程式碼，並檢查其變數。 這些功能更強大的功能可用於許多案例中，特別是下列項目：

* 您正嘗試找出您的程式碼的執行階段錯誤，但卻無法使用方法與先前所討論的工具。

* 您想要驗證您的程式碼，也就是，以確定它是能如您預期的方式，進行您想要它執行時，請觀看它。

    它是執行時監看您的程式碼會更有意義。 您可以進一步了解您的程式碼這種方式，和之前在資訊清單任何明顯的徵狀，則通常可以識別錯誤。

若要了解如何使用偵錯工具的基本功能，請參閱[偵錯適用於徹底初學者](../debugger/debugging-absolute-beginners.md)。

## <a name="fix-performance-issues"></a>修正效能問題

Bug 的另一種包含效率不佳的程式碼，使您的應用程式執行速度變慢，或使用太多記憶體。 一般而言，最佳化效能是您稍後在應用程式開發中執行的項目。 不過，您可能會遇到效能問題初期 （例如，您看到您的應用程式的某個部分執行速度很慢），而且您可能需要及早測試您的應用程式的程式碼剖析工具。 如需有關程式碼剖析工具，例如 CPU 使用量工具以及記憶體分析器的詳細資訊，請參閱 <<c0> [ 第一次查看程式碼剖析工具](../profiling/profiling-feature-tour.md)。

## <a name="sample-code"></a> 範例程式碼

下列程式碼有一些您可以使用 Visual Studio IDE 來修正的 bug。 應用程式是簡單的應用程式，模擬取得的 JSON 資料，從某項作業，還原序列化至物件，資料與新的資料來更新簡單的清單。

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON_DotNetCore
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

## <a name="next-steps"></a>後續步驟

在本文中，您已了解如何避免並修正程式碼中的許多常見的錯誤，以及使用偵錯工具的時機。 接下來，深入了解使用 Visual Studio 偵錯工具若要修正的 bug。

> [!div class="nextstepaction"]
> [適合完全初學者的偵錯](../debugger/debugging-absolute-beginners.md)
