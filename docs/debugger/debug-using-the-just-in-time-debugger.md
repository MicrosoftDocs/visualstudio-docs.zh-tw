---
title: 使用 Just-In-Time 偵錯工具進行偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 09/24/18
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a2e6cfbd6d26d575bab5d7592f320779ffd8888
ms.sourcegitcommit: 000cdd1e95dd02e99a7c7c1a34c2f8fba6a632af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168392"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>在 Visual Studio 中使用 Just-In-Time 偵錯工具進行偵錯
在 Just-in-time 偵錯 Visual Studio 會自動啟動 Visual Studio 外部執行的應用程式中發生的例外狀況或損毀時。 這可讓您測試您的應用程式，若未執行 Visual Studio，並開始發生問題時，使用 Visual Studio 偵錯。

在 Just-in-time 偵錯適用於 Windows 桌面應用程式。 不適用於通用 Windows 應用程式，並不適用於裝載在原生應用程式，例如視覺化檢視中的 managed 程式碼。

> [!TIP]
> 如果您只想知道如何回應的時間只需偵錯工具 對話方塊中，請參閱 <<c0> [ 本主題](../debugger/just-in-time-debugging-in-visual-studio.md)。

##  <a name="BKMK_Enabling"></a> 啟用或停用 Just In Time 偵錯
您可以啟用或停用 Just 時間從 Visual Studio 偵錯**工具 > 選項** 對話方塊。

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>若要啟用或停用 Just-In-Time 偵錯

1.  使用系統管理員權限開啟 Visual Studio (以滑鼠右鍵按一下，然後選擇 **系統管理員身分執行**)。

    啟用或停用 Just In Time 偵錯設定登錄機碼，並可能需要系統管理員權限，才能變更該金鑰。

2. 在 [ **工具** ] 功能表上按一下 [ **選項**]。

2.  在 **選項**對話方塊方塊中，展開**偵錯**節點。

3.  在 **偵錯**節點中，選取**Just In Time**。

    ![啟用或停用 JIT 偵錯](../debugger/media/dbg-jit-enable-or-disable.png "啟用或停用 JIT 偵錯")

4.  在 **啟用的 Just-In-Time 偵錯這些程式碼類型**方塊中，選取或清除相關的程式類型：**受控**，**原生**，或**指令碼**.

5.  按一下 [確定 **Deploying Office Solutions**]。

    如果您啟用的時間只需偵錯工具，但您看不到它在應用程式當機或例外狀況，請參閱 <<c0> [ 恰好時間偵錯錯誤](#jit_errors)。

即使電腦上已沒有安裝 Visual Studio，Just-In-Time 偵錯可能仍然為啟用狀態。 未安裝 Visual Studio 時，您無法停用 Just 時間從 Visual Studio 偵錯**選項** 對話方塊。 在此情況下，您可以編輯 Windows 登錄來停用 Just-In-Time 偵錯。

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>若要編輯登錄來停用 Just-In-Time 偵錯

1.  在 [**啟動**] 功能表中，搜尋並執行 `regedit.exe`

2.  在 [**登錄編輯程式**] 視窗中，找出並刪除下列登錄項目：

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework\DbgManagedDebugger

    ![登錄機碼 JIT](../debugger/media/dbg-jit-registry.png "JIT 登錄機碼")

3.  如果您的電腦執行 64 位元作業系統，也刪除下列登錄項目：

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\。NETFramework\DbgManagedDebugger

4.  請小心不要刪除或變更其他任何登錄機碼。

5.  關閉**登錄編輯程式**視窗。

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>若要啟用 Windows Form 的 Just-In-Time 偵錯

1.  根據預設，Windows Forms 應用程式具有最上層的例外狀況處理常式，允許程式在能夠復原時繼續執行。 比方說，如果您的 Windows Forms 應用程式擲回未處理的例外狀況，您會看到一個對話方塊，如下所示：

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     若要啟用 Just In Time 偵錯 Windows Form 應用程式，您必須執行下列額外步驟：

2.  設定`jitDebugging`值加入`true`中`system.windows.form`machine.config 區段或*\<應用程式名稱 >*.exe.config 檔案：

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  在 C++ Windows Form 應用程式中，您也必須在 .config 檔或您的程式碼中設定 `DebuggableAttribute`。 如果您使用編譯[/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) ，而不[/Og](/cpp/build/reference/og-global-optimizations)，編譯器會將這個屬性設為您。 然而，如果您要對非最佳化的發行組建進行偵錯，則必須自行完成此設定。 若要這樣做，您可以將下面這行程式碼加入至應用程式的 AssemblyInfo.cpp 檔案。

    ```cpp
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     如需詳細資訊，請參閱<xref:System.Diagnostics.DebuggableAttribute>。

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">使用-Just-in-time 偵錯
 本節說明可執行檔就會擲回例外狀況時，會發生什麼事。

 您必須遵循下列步驟安裝的 Visual Studio。 如果您沒有 Visual Studio，您可以下載免費[Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)。

 請確定的時間，只需偵錯[啟用](#BKMK_Enabling)。

 基於本章節的目的，我們要在擲回的 Visual Studio 中進行 C# 主控台應用程式[NullReferenceException](/dotnet/api/system.nullreferenceexception)。

 在 Visual Studio 中，建立 C# 主控台應用程式 (**檔案 > 新增 > 專案 > Visual C# > 主控台應用程式**) 名為**ThrowsNullException**。 如需在 Visual Studio 中建立專案的詳細資訊，請參閱[逐步解說： 建立簡單的應用程式](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)。

 當專案在 Visual Studio 中開啟時，請開啟 Program.cs 檔案。 取代為下列程式碼，這會列印到主控台一行，然後擲回 NullReferenceException 的 main （） 方法：

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  為了讓這個程序運作[release 組態](../debugger/how-to-set-debug-and-release-configurations.md)，您必須關閉[Just My Code](../debugger/just-my-code.md)。 在 Visual Studio 中，按一下**工具 > 選項**。 在 **選項**對話方塊中，選取**偵錯**。 移除核取**啟用 Just My Code**。

 建置方案 (在 Visual Studio 中，選擇**建置 > 重建方案**)。 您可以選擇偵錯或發行組態 (選擇**偵錯**取得完整的偵錯體驗)。 如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。

 建置程序會建立可執行檔的 ThrowsNullException.exe。 您可以在您用來建立 C# 專案的資料夾下找到它： **...\ThrowsNullException\ThrowsNullException\bin\Debug**或是 **...\ThrowsNullException\ThrowsNullException\bin\Release**。

 按兩下 ThrowsNullException.exe。 您應該會看到如下的命令 視窗：

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 後幾秒鐘之後，會出現錯誤視窗：

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 請勿按下**取消**！ 幾秒之後，您應該會看到兩個按鈕**偵錯**並**關閉程式**。 按一下 **偵錯**。

> [!CAUTION]
>  如果您的應用程式包含不受信任的程式碼，會出現安全性警告對話方塊。 這個對話方塊可讓您決定是否繼續偵錯。 在繼續偵錯之前，請決定這是否為可以信任的程式碼。 這是您自行撰寫的程式碼嗎？ 您信任撰寫這個程式碼的人嗎？ 如果應用程式在遠端電腦上執行，您認得它的處理序名稱嗎？ 即使應用程式在本機執行，也不代表絕對可以信任。 請考慮在您的電腦上執行的惡意程式碼的可能性。 如果您決定，程式碼您即將要偵錯是值得信任，按一下**偵錯**。 否則，請按一下**不要偵錯**。

 **Visual Studio Just-In-Time 偵錯工具** 視窗隨即出現：

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 底下**可能的偵錯工具**，您應該會看到**Microsoft Visual Studio 的新執行個體<available version>** 列已選取。 如果已選取，現在請對它進行選取。

 底部的視窗中，在**您要使用選取的偵錯工具進行偵錯嗎？**，按一下**是**。

 與執行已停止的行，則會擲回例外狀況，在 Visual Studio 中的新執行個體中開啟 ThrowsNullException 專案：

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 您可以開始在此時偵錯。 如果這是實際的應用程式時，您必須了解為什麼程式碼會擲回例外狀況。

## <a name="jit_errors"></a> 在 Just-in-time 偵錯錯誤
 如果您沒有看到 [] 對話方塊中，程式損毀，而且需要啟用此功能時，這可能因為電腦上的 Windows 錯誤報告設定。 請務必新增**已停用**下列登錄機碼值，並將值設為 1:

* HKLM\Software\Microsoft\Windows\Windows 錯誤報告
* HKLM\Software\WOW6432Node\Microsoft\Windows\Windows 錯誤報告
 
如需有關這些設定的詳細資訊，請參閱[。WER 設定](https://docs.microsoft.com/windows/desktop/wer/wer-settings)。

此外，您可能會看到下列錯誤訊息與 Just In Time 相關聯的偵錯。

- **無法附加到損毀處理序。指定的程式不是 Windows 或 MS-DOS 程式。**

    當您嘗試附加至另一個使用者身分執行處理序時，就會發生此錯誤。

    若要解決這個問題，請啟動 Visual Studio 中，開啟**附加至處理序**對話方塊中，從**偵錯**功能表，然後尋找程序，您想要在偵錯**可用的處理序**清單。 如果您不知道處理序的名稱，看看**Visual Studio Just-In-Time 偵錯工具**對話方塊，然後記處理序識別碼。 選取中的程序**可用的處理序**清單，然後按一下**附加**。 在 [ **Visual Studio Just-In-Time 偵錯工具**] 對話方塊中，按一下**否**關閉對話方塊。

- **無法啟動偵錯工具，因為沒有使用者登入。**

    當 Just-In-Time 偵錯嘗試在沒有使用者登入主控台的電腦上啟動 Visual Studio 時，就會發生此錯誤。 因為沒有使用者登入，所以沒有使用者工作階段可顯示 [Just-In-Time 偵錯] 對話方塊。

    若要修正這個問題，請登入該電腦。

- **未註冊的類別。**

    這個錯誤表示偵錯工具嘗試建立的 COM 類別尚未登錄，可能是因為安裝問題所致。

    若要修正這個問題，請使用安裝磁碟重新安裝或修復 Visual Studio 安裝。

## <a name="see-also"></a>另請參閱
 [偵錯工具安全性](../debugger/debugger-security.md)[偵錯工具基本概念](../debugger/getting-started-with-the-debugger.md)[只要時間，偵錯、 選項對話方塊](../debugger/just-in-time-debugging-options-dialog-box.md)[安全性警告： 附加至不受信任的使用者所擁有的處理序可能會危險。如果下面的資訊看起來有問題，或者您並不確定，請不要附加至此處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
