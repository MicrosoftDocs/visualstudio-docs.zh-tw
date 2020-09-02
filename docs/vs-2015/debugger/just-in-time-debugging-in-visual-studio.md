---
title: Just-In-Time 偵錯
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690600"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Visual Studio 中的 Just-In-Time 偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當在 Visual Studio 外部執行的應用程式中發生例外狀況或損毀時，即時偵錯工具會自動啟動 Visual Studio。 這可讓您在 Visual Studio 未執行時測試您的應用程式，並在發生問題時開始使用 Visual Studio 進行偵錯工具。

適用于 Windows 桌面應用程式的即時偵錯工具。 它不適用於 Windows 通用應用程式，也不適用於裝載于原生應用程式（例如視覺化程式）中的 managed 程式碼。

## <a name="did-the-just-in-time-debugger-dialog-box-appear-when-trying-to-run-an-app"></a><a name="BKMK_Scenario"></a> 當您嘗試執行應用程式時，會出現 [即時偵錯工具] 對話方塊嗎？

當您看到 [Visual Studio 即時偵錯工具] 對話方塊時，您應該採取的動作取決於您嘗試執行的動作：

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>如果您想要清除此對話方塊並正常地執行應用程式

1. 如果您已 Visual Studio 安裝 (，或您先前已安裝並移除) ，請 (Advanced users) ，請 [停用即時調試](#BKMK_Enabling) 程式，然後再次嘗試執行應用程式。

2. 如果您是在 Internet Explorer 中執行 web 應用程式，請停用腳本偵錯工具。

    在 [網際網路選項] 對話方塊中停用腳本調試。 您可以從**主控台**  /  **網路和網際網路**  /  **網際網路選項**來存取此選項 (確切的步驟取決於您的 Windows 版本和 Internet Explorer) 。

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. 重新開啟您發現錯誤的網頁。 如果這無法解決問題，請洽詢 web 應用程式的擁有者以修正問題。

4. 如果您執行的是另一種 Windows 應用程式，則必須與應用程式的擁有者聯繫以修正錯誤，然後重新安裝應用程式的固定版本。

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>如果您想要修正或偵測 (advanced users 的錯誤) 

- 您必須 [安裝 Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) ，才能查看錯誤的詳細資訊，並嘗試進行調試。 如需詳細指示，請參閱 [使用 JIT](#BKMK_Using_JIT) 。 如果您無法解決錯誤並修正應用程式，請聯繫應用程式的擁有者以解決錯誤。

## <a name="enable-or-disable-just-in-time-debugging"></a><a name="BKMK_Enabling"></a> 啟用或停用即時調試
 您可以從 Visual Studio [ **工具]/[選項** ] 對話方塊啟用或停用即時調試。

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>若要啟用或停用 Just-In-Time 偵錯

1. 開啟 Visual Studio。 在 **[工具]** 功能表上，按一下 **[選項]** 。

2. 在 [ **選項** ] 對話方塊中，選取 [ **調試** ] 資料夾。

3. 在 [ **調試** ] 資料夾中，選取 [ **即時** ] 頁面。

4. 在 [ **啟用這些類型程式碼的即時調試** 程式] 方塊中，選取或清除相關的程式類型： [ **Managed**]、[ **原生**] 或 [ **腳本**]。

    若要在啟用 Just-In-Time 偵錯之後加以停用，您必須以系統管理員權限執行。 啟用 Just-In-Time 偵錯會設定一個登錄機碼，您必須使用系統管理員權限才能變更該機碼。

5. 按一下 [確定]  。

   即使電腦上已沒有安裝 Visual Studio，Just-In-Time 偵錯可能仍然為啟用狀態。 未安裝 Visual Studio 時，您無法從 [Visual Studio **選項** ] 對話方塊中停用即時偵錯工具。 在此情況下，您可以編輯 Windows 登錄來停用 Just-In-Time 偵錯。

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>若要編輯登錄來停用 Just-In-Time 偵錯

1. 在 [ **開始** ] 功能表上，搜尋並執行 `regedit.exe`

2. 在 [ **登錄編輯程式** ] 視窗中，找出並刪除下列登錄專案：

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger

3. 如果您的電腦執行的是64位的作業系統，也請刪除下列登錄專案：

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger

4. 請小心不要刪除或變更其他任何登錄機碼。

5. 關閉 [登錄編輯程式]**** 視窗。

> [!NOTE]
> 如果您嘗試停用伺服器端應用程式的即時偵錯工具，而這些步驟無法解決問題，請關閉 IIS 應用程式設定中的伺服器端偵錯工具，然後再試一次。

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>若要啟用 Windows Form 的 Just-In-Time 偵錯

1. 根據預設，Windows Forms 應用程式具有最上層的例外狀況處理常式，允許程式在能夠復原時繼續執行。 例如，如果您的 Windows Forms 應用程式擲回未處理的例外狀況，您會看到如下的對話方塊：

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     若要啟用 Windows Forms 應用程式的即時偵錯工具，您必須執行下列額外步驟：

2. `jitDebugging` `true` 在 `system.windows.form` machine.config 或.exe.config 檔案的區段中，將值設定為 *\<application name>* ：

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. 在 C++ Windows Form 應用程式中，您也必須在 .config 檔或您的程式碼中設定 `DebuggableAttribute`。 如果您使用 [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) 而且未使用 [/Og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435) 進行編譯，則編譯器將會設定這個屬性 (Attribute)。 然而，如果您要對非最佳化的發行組建進行偵錯，則必須自行完成此設定。 若要這樣做，您可以將下面這行程式碼加入至應用程式的 AssemblyInfo.cpp 檔案。

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     如需詳細資訊，請參閱<xref:System.Diagnostics.DebuggableAttribute>。

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">使用即時調試
 本節說明當可執行檔擲回例外狀況時，會發生什麼事。

 您必須安裝 Visual Studio，才能遵循這些步驟。 如果您沒有 Visual Studio，可以下載免費的 [Visual Studio 2015 版的版](https://visualstudio.microsoft.com/vs/older-downloads/)。

 當您安裝 Visual Studio 時，預設會啟用 Just-In-Time 偵錯。

 基於本節的目的，我們會在擲回的 Visual Studio 中建立 c # 主控台應用程式 <xref:System.NullReferenceException> 。

 在 Visual Studio 中，建立 c # 主控台應用程式 (檔案 **/新的/專案/Visual c #/主控台應用程式**) 名為 **ThrowsNullException**。 如需在 Visual Studio 中建立專案的詳細資訊，請參閱 [逐步解說：建立簡單的應用程式](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)。

 當專案在 Visual Studio 中開啟時，開啟 Program.cs 檔案。 以下列程式碼取代主要 ( # A1 方法，它會將一行列印到主控台，然後擲回 NullReferenceException：

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> 您必須關閉[Just My Code](../debugger/just-my-code.md)，才能讓此程式在[發行](../debugger/how-to-set-debug-and-release-configurations.md)設定中運作。 在 Visual Studio 中，按一下 [ **工具]/[選項**]。 在 [ **選項** ] 對話方塊中，選取 [ **調試**]。 從 [ **啟用 Just My Code**] 移除檢查。

 在 Visual Studio 中建立方案 (，選擇 [ **建立/重建方案**) ]。 您可以選擇 Debug 或 Release configuration。 如需組建設定的詳細資訊，請參閱 [瞭解組建](../ide/understanding-build-configurations.md)設定。

 組建進程會建立可執行檔 ThrowsNullException.exe。 您可以在建立 c # 專案的資料夾下找到它： **. ..\ThrowsNullException\ThrowsNullException\bin\Debug** 或 **. ..\ThrowsNullException\ThrowsNullException\bin\Release**。

 按兩下 [ThrowsNullException.exe]。 您應該會看到如下所示的命令視窗：

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 幾秒鐘之後，就會出現錯誤視窗：

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 不要按 [ **取消**]！ 幾秒鐘後，您應該會看到兩個按鈕： **Debug** 和 **Close 程式**。 按一下 [ **Debug**]。

> [!CAUTION]
> 如果您的應用程式包含未受信任的程式碼，則會出現含有安全性警告的對話方塊。 這個對話方塊可讓您決定是否繼續偵錯。 在繼續偵錯之前，請決定這是否為可以信任的程式碼。 這是您自行撰寫的程式碼嗎？ 您信任撰寫這個程式碼的人嗎？ 如果應用程式在遠端電腦上執行，您認得它的處理序名稱嗎？ 即使應用程式在本機執行，也不代表絕對可以信任。 請考慮在您的電腦上執行惡意程式碼的可能性。 如果您決定要 debug 的程式碼是可信任的，請按一下 [ **debug**]。 否則，請按一下 [ **不 Debug**]。

 此時會出現 **Visual Studio 的即時偵錯工具** 視窗：

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 在 [ **可能的調試**程式] 下，您應該會看到已選取 Microsoft Visual Studio 2015 行的 **新實例** 。 如果尚未選取，請立即選取。

 在視窗底部的 [ **您要使用選取的偵錯工具進行 debug？**] 底下，按一下 **[是**]。

 ThrowsNullException 專案會在 Visual Studio 的新實例中開啟，並在擲回例外狀況的那一行停止執行：

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 您可以在此開始進行調試。 如果這是實際的應用程式，您就必須找出程式碼擲回例外狀況的原因。

## <a name="just-in-time-debugging-errors"></a>Just-In-Time 偵錯的錯誤
 如果程式損毀時未看到對話方塊，這可能是電腦上 Windows 錯誤報告設定所致。 如需詳細資訊，請參閱 [。WER 設定](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx)。

 您可能會看見下列與 Just-in-Time 偵錯相關的錯誤訊息。

- **無法附加至損毀進程。指定的程式不是 Windows 或 MS-DOS 程式。**

     當您嘗試附加至以其他使用者的形式執行的進程時，就會發生這個錯誤。

     若要解決這個問題，請啟動 Visual Studio，從 [**調試**程式] 功能表開啟 [**附加至進程**] 對話方塊，然後在 [**可用的進程**] 清單中尋找您想要進行偵錯工具的進程。 如果您不知道進程的名稱，請查看 **Visual Studio 的即時偵錯工具** 對話方塊，並記下處理序識別碼。 在 [ **可使用的進程** ] 清單中選取該進程，然後按一下 [ **附加**]。 在 [ **Visual Studio 即時偵錯工具** ] 對話方塊中，按一下 [ **否** ] 關閉對話方塊。

- **由於沒有使用者登入，無法啟動偵錯工具。**

     當 Just-In-Time 偵錯嘗試在沒有使用者登入主控台的電腦上啟動 Visual Studio 時，就會發生此錯誤。 因為沒有使用者登入，所以沒有使用者工作階段可顯示 [Just-In-Time 偵錯] 對話方塊。

     若要修正這個問題，請登入該電腦。

- **類別未登錄。**

     這個錯誤表示偵錯工具嘗試建立的 COM 類別尚未登錄，可能是因為安裝問題所致。

     若要修正這個問題，請使用安裝磁碟重新安裝或修復 Visual Studio 安裝。

## <a name="see-also"></a>另請參閱
 調試[程式安全性](../debugger/debugger-security.md)[偵錯工具基本概念](../debugger/debugger-basics.md)即時[，偵錯工具，選項對話方塊](../debugger/just-in-time-debugging-options-dialog-box.md)[安全性警告：附加至不受信任的使用者所擁有的進程可能會造成危險。如果下列資訊看起來很可疑，或您不確定，請不要附加至此進程](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)
