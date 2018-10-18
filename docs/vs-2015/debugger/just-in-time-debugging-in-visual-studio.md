---
title: 在 Just-in-time 偵錯在 Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 606f0129d49e8d5b8f07e6c8fac60fa5029a4828
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294043"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Visual Studio 中的 Just-In-Time 偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Just-in-time 偵錯 Visual Studio 會自動啟動 Visual Studio 外部執行的應用程式中發生的例外狀況或損毀時。 這可讓您測試您的應用程式，若未執行 Visual Studio，並開始發生問題時，使用 Visual Studio 偵錯。

在 Just-in-time 偵錯適用於 Windows 桌面應用程式。 不適用於 Windows 通用應用程式，並不適用於裝載在原生應用程式，例如視覺化檢視中的 managed 程式碼。

## <a name="BKMK_Scenario"></a> 未在時間只要偵錯工具 對話方塊出現時嘗試執行應用程式嗎？

您會看到 Visual Studio 只要時間時，您應該採取的動作取決於您嘗試執行的偵錯工具 對話方塊中：

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>如果您想要移除 [] 對話方塊中，而只是應用程式正常執行

1. （進階的使用者）如果您已安裝的 Visual Studio （或您擁有先前安裝它，並將其移除），[停用 Just in Time 偵錯](#BKMK_Enabling)，然後再試一次執行應用程式。

2. 如果您在 Internet Explorer 中執行的 web 應用程式，停用指令碼偵錯。

    停用指令碼偵錯 [網際網路選項] 對話方塊中。 您可以存取這個屬性從**控制台中** / **網路和網際網路** / **網際網路選項**（的確切步驟取決於您的版本Windows 和 Internet Explorer）。

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. 重新開啟您在發現錯誤所在的網頁。 如果這樣做無法解決問題，請連絡擁有者的 web 應用程式以修正此問題。

4. 如果您正在執行另一種 Windows 應用程式，您必須連絡應用程式的擁有者，修正錯誤，然後再重新安裝應用程式的固定的版本。

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>如果您想要修正或偵錯錯誤 （進階使用者）

- 您必須擁有[安裝 Visual Studio](https://www.microsoft.com/download/details.aspx?id=48146)來檢視有關錯誤的詳細的資訊，並嘗試進行偵錯。 請參閱[使用 JIT](#BKMK_Using_JIT)如需詳細指示。 如果您不能解決此錯誤並修正應用程式，請連絡應用程式的擁有者，來解決這個錯誤。
  
##  <a name="BKMK_Enabling"></a> 啟用或停用 Just In Time 偵錯  
 您可以啟用或停用 Just 時間從 Visual Studio 偵錯**工具 / 選項** 對話方塊。  
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>若要啟用或停用 Just-In-Time 偵錯  
  
1.  開啟 Visual Studio。 在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2.  在 **選項**對話方塊中，選取**偵錯**資料夾。  
  
3.  在 **偵錯**資料夾中，選取**Just In Time**頁面。  
  
4.  在 **啟用的 Just-In-Time 偵錯這些程式碼類型**方塊中，選取或清除相關的程式類型：**受控**，**原生**，或**指令碼**.  
  
     若要在啟用 Just-In-Time 偵錯之後加以停用，您必須以系統管理員權限執行。 啟用 Just-In-Time 偵錯會設定一個登錄機碼，您必須使用系統管理員權限才能變更該機碼。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
 即使電腦上已沒有安裝 Visual Studio，Just-In-Time 偵錯可能仍然為啟用狀態。 未安裝 Visual Studio 時，您無法停用 Just 時間從 Visual Studio 偵錯**選項** 對話方塊。 在此情況下，您可以編輯 Windows 登錄來停用 Just-In-Time 偵錯。  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>若要編輯登錄來停用 Just-In-Time 偵錯  
  
1.  在 [**啟動**] 功能表中，搜尋並執行 `regedit.exe`  
  
2.  在 [**登錄編輯程式**] 視窗中，找出並刪除下列登錄項目：  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework\DbgManagedDebugger  
  
3.  如果您的電腦執行 64 位元作業系統，也刪除下列登錄項目：  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\。NETFramework\DbgManagedDebugger  
  
4.  請小心不要刪除或變更其他任何登錄機碼。  
  
5.  關閉**登錄編輯程式**視窗。  
  
> [!NOTE]
>  如果您嘗試停用 Just 時間的伺服器端應用程式的偵錯，而且這些步驟未能解決此問題，請關閉伺服器端偵錯 IIS 應用程式設定中，然後重試。  
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>若要啟用 Windows Form 的 Just-In-Time 偵錯  
  
1.  根據預設，Windows Forms 應用程式具有最上層的例外狀況處理常式，允許程式在能夠復原時繼續執行。 比方說，如果您的 Windows Forms 應用程式擲回未處理的例外狀況，您會看到一個對話方塊，如下所示：  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     若要啟用 Just In Time 偵錯 Windows Form 應用程式，您必須執行下列額外步驟：  
  
2.  設定`jitDebugging`值加入`true`中`system.windows.form`machine.config 區段或*\<應用程式名稱 >*.exe.config 檔案：  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  在 C++ Windows Form 應用程式中，您也必須在 .config 檔或您的程式碼中設定 `DebuggableAttribute`。 如果您使用編譯[/Zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) ，而不[/Og](http://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435)，編譯器會將這個屬性設為您。 然而，如果您要對非最佳化的發行組建進行偵錯，則必須自行完成此設定。 若要這樣做，您可以將下面這行程式碼加入至應用程式的 AssemblyInfo.cpp 檔案。  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     如需詳細資訊，請參閱<xref:System.Diagnostics.DebuggableAttribute>。  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">使用-Just-in-time 偵錯  
 本節說明可執行檔就會擲回例外狀況時，會發生什麼事。  
  
 您必須遵循下列步驟安裝的 Visual Studio。 如果您沒有 Visual Studio，您可以下載免費[Visual Studio 2015 Community Edition](https://www.microsoft.com/download/details.aspx?id=48146)。  
  
 當您安裝 Visual Studio 時，預設會啟用 Just-In-Time 偵錯。  
  
 基於本章節的目的，我們要在擲回的 Visual Studio 中進行 C# 主控台應用程式<xref:System.NullReferenceException>。  
  
 在 Visual Studio 中，建立 C# 主控台應用程式 (**檔案 / 新增 / 專案 / Visual C# / 主控台應用程式**) 名為**ThrowsNullException**。 如需在 Visual Studio 中建立專案的詳細資訊，請參閱[逐步解說： 建立簡單的應用程式](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)。  
  
 當專案在 Visual Studio 中開啟時，請開啟 Program.cs 檔案。 取代為下列程式碼，這會列印到主控台一行，然後擲回 NullReferenceException 的 main （） 方法：  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  為了讓這個程序運作[release 組態](../debugger/how-to-set-debug-and-release-configurations.md)，您必須關閉[Just My Code](../debugger/just-my-code.md)。 在 Visual Studio 中，按一下**工具 / 選項**。 在 **選項**對話方塊中，選取**偵錯**。 移除核取**啟用 Just My Code**。  
  
 建置方案 (在 Visual Studio 中，選擇**建置 / 重建方案**)。 您可以選擇偵錯或發行組態。 如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。  
  
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
  
 底下**可能的偵錯工具**，您應該會看到**Microsoft Visual Studio 2015 的新執行個體**列已選取。 如果已選取，現在請對它進行選取。  
  
 底部的視窗中，在**您要使用選取的偵錯工具進行偵錯嗎？**，按一下**是**。  
  
 與執行已停止的行，則會擲回例外狀況，在 Visual Studio 中的新執行個體中開啟 ThrowsNullException 專案：  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 您可以開始在此時偵錯。 如果這是實際的應用程式時，您必須了解為什麼程式碼會擲回例外狀況。  
  
## <a name="just-in-time-debugging-errors"></a>Just-In-Time 偵錯的錯誤  
 如果您沒有看到 [] 對話方塊中，程式損毀時，這可能因為電腦上的 Windows 錯誤報告設定。 如需詳細資訊，請參閱[。WER 設定](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx)。  
  
 您可能會看見下列與 Just-in-Time 偵錯相關的錯誤訊息。  
  
-   **無法附加到損毀處理序。指定的程式不是 Windows 或 MS-DOS 程式。**  
  
     當您嘗試附加至另一個使用者身分執行處理序時，就會發生此錯誤。  
  
     若要解決這個問題，請啟動 Visual Studio 中，開啟**připojit k procesu**對話方塊中，從**偵錯**功能表，然後尋找程序，您想要在偵錯**可用的處理序**清單。 如果您不知道處理序的名稱，看看**Visual Studio Just-In-Time 偵錯工具**對話方塊，然後記處理序識別碼。 選取中的程序**可用的處理序**清單，然後按一下**附加**。 在 [ **Visual Studio Just-In-Time 偵錯工具**] 對話方塊中，按一下**否**關閉對話方塊。  
  
-   **無法啟動偵錯工具，因為沒有使用者登入。**  
  
     當 Just-In-Time 偵錯嘗試在沒有使用者登入主控台的電腦上啟動 Visual Studio 時，就會發生此錯誤。 因為沒有使用者登入，所以沒有使用者工作階段可顯示 [Just-In-Time 偵錯] 對話方塊。  
  
     若要修正這個問題，請登入該電腦。  
  
-   **未註冊的類別。**  
  
     這個錯誤表示偵錯工具嘗試建立的 COM 類別尚未登錄，可能是因為安裝問題所致。  
  
     若要修正這個問題，請使用安裝磁碟重新安裝或修復 Visual Studio 安裝。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)   
 [只是時間，偵錯、 選項對話方塊](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [安全性警告︰附加至未受信任的使用者所擁有的處理序可能會造成危險。如果下面的資訊看起來有問題，或者您並不確定，請不要附加至此處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)



