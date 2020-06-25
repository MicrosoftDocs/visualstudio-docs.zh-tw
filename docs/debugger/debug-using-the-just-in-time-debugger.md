---
title: 使用即時偵錯工具進行 Debug |Microsoft Docs
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40b6a0e43a8d0980615087c946e5dd14deef1b0b
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350572"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>在 Visual Studio 中使用即時偵錯工具進行 Debug

當應用程式在外部執行 Visual Studio 錯誤或損毀時，即時的偵測可以自動啟動 Visual Studio。 有了即時的偵錯工具，您就可以在 Visual Studio 外部測試應用程式，並開啟 Visual Studio，以便在發生問題時開始進行偵測。

即時的偵錯工具適用于 Windows 桌面應用程式。 它不適用於通用 Windows 應用程式，或裝載于原生應用程式中的 managed 程式碼，例如視覺化檢視。

> [!TIP]
> 如果您只想要停止 [即時偵錯工具] 對話方塊，但未安裝 Visual Studio，請參閱[停用即時偵錯工具](../debugger/just-in-time-debugging-in-visual-studio.md)。 如果您已安裝 Visual Studio，可能需要[從 Windows 登錄中停用即時](#disable-just-in-time-debugging-from-the-windows-registry)的偵測。

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a>在 Visual Studio 中啟用或停用即時調試

>[!NOTE]
>若要啟用或停用即時的偵錯工具，您必須以系統管理員身分執行 Visual Studio。 啟用或停用即時偵錯工具會設定登錄機碼，而且可能需要系統管理員許可權才能變更該金鑰。 若要以系統管理員身分開啟 Visual Studio，請以滑鼠右鍵按一下 Visual Studio 應用程式，然後選擇 [**以系統管理員身分執行**]。

您可以從 [Visual Studio**工具**  >  ] [**選項**] （或 [ **Debug**  >  **選項**]）對話方塊設定即時的調試。

**若要啟用或停用即時調試：**

1. 在 [**工具**] 或 [**調試**] 功能表上，選取 [ **Options**  >  **Debugging**  >  **即時**調試] 選項。

   ![啟用或停用 JIT 偵錯](../debugger/media/dbg-jit-enable-or-disable.png "啟用或停用 JIT 偵錯")

1. 在 [**為這些類型的程式碼啟用即時調試**程式] 方塊中，選取您想要進行即時偵錯工具的程式碼類型： [ **Managed**]、[**原生**] 和/或 [**腳本**]。

1. 選取 [確定]。

如果您啟用即時偵錯工具，但在應用程式損毀或錯誤時不會開啟，請參閱[疑難排解即時](#jit_errors)的偵測。

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>從 Windows 登錄停用即時調試

即使電腦上已沒有安裝 Visual Studio，Just-In-Time 偵錯可能仍然為啟用狀態。 如果不再安裝 Visual Studio，您可以藉由編輯 Windows 登錄來停用即時的偵錯工具。

**若要藉由編輯登錄來停用即時的偵錯工具：**

1. 從 Windows 的 [**開始**] 功能表中，執行 [**登錄編輯程式**] （*regedit.exe*）。

2. 在 [**登錄編輯程式**] 視窗中，找出並刪除下列登錄專案：

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JIT 登錄機碼](../debugger/media/dbg-jit-registry.png "JIT 登錄機碼")

3. 如果您的電腦正在執行64位的作業系統，也請刪除下列登錄專案：

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    請確定不要刪除或變更任何其他登錄機碼。

5. 關閉 [登錄編輯程式]**** 視窗。

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>啟用 Windows Form 的即時調試

根據預設，Windows Form 應用程式具有最上層的例外狀況處理常式，可讓應用程式在可以復原的情況下繼續運作。 如果 Windows Forms 應用程式擲回未處理的例外狀況，則會顯示下列對話方塊：

![Windows Form 未處理的例外狀況](../debugger/media/windowsformsunhandledexception.png "Windows Form 未處理的例外狀況")

若要啟用即時調試，而不是標準的 Windows Form 錯誤處理，請新增下列設定：

- 在 `system.windows.forms` *machine.config*或* \<app name>.exe.config*檔案的區段中，將值設定 `jitDebugging` 為 `true` ：

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- 在 c + + Windows Form 應用程式中，也會 `DebuggableAttribute` `true` 在 *.config*檔案或您的程式碼中設定為。 如果您使用 [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) 而且未使用 [/Og](/cpp/build/reference/og-global-optimizations) 進行編譯，則編譯器將會設定這個屬性 (Attribute)。 不過，如果您想要進行非優化的發行組建，您必須 `DebuggableAttribute` 在應用程式的*AssemblyInfo*檔中新增下列這行：

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   如需詳細資訊，請參閱 <xref:System.Diagnostics.DebuggableAttribute> 。

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>使用即時調試
這個範例會逐步引導您在應用程式擲回錯誤時進行即時調試。

- 您必須安裝 Visual Studio，才能遵循這些步驟。 如果您沒有 Visual Studio，可以下載免費的[Visual Studio Community 版本](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)。

- 請確定已在 [**工具**] [選項] [立即] [即時調試] 中[啟用](#BKMK_Enabling)即時調試  >  **Options**  >  **Debugging**  >  ** **。

在此範例中，您會在 Visual Studio 中建立 c # 主控台應用程式，以擲回[NullReferenceException](/dotnet/api/system.nullreferenceexception)。

1. 在 Visual Studio 中，建立名為 ThrowsNullException 的 c # 主控台應用**程式（檔案**  >  **新**  >  **專案**  >  **Visual c #**  >  **主控台應用程式**）。 *ThrowsNullException* 如需在 Visual Studio 中建立專案的詳細資訊，請參閱[逐步解說：建立簡單的應用程式](../get-started/csharp/tutorial-wpf.md)。

1. 當專案在 Visual Studio 中開啟時，請開啟*Program.cs*檔案。 將 Main （）方法取代為下列程式碼，以將一行列印到主控台，然後擲回 NullReferenceException：

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. 若要建立解決方案，請選擇 [ **Debug** ] （預設值）或 [**發行**] 設定，然後選取 [**建立**  >  **重建解決方案**]。

   > [!NOTE]
   > - 選擇 [ **Debug**設定] 以取得完整的偵錯工具體驗。
   > - 如果您選取 [[發行](../debugger/how-to-set-debug-and-release-configurations.md)設定]，則必須關閉[Just My Code](../debugger/just-my-code.md) ，才能讓此程式正常執行。 在 [**工具**  >  **選項**] 底下  >  ** **，取消選取 [**啟用 Just My Code**]。

   如需組建設定的詳細資訊，請參閱[瞭解組建](../ide/understanding-build-configurations.md)設定。

1. 在您的 c # 專案資料夾中開啟建立的應用程式*ThrowsNullException.exe* （*. ..\ThrowsNullException\ThrowsNullException\bin\Debug*或 *. ..\ThrowsNullException\ThrowsNullException\bin\Release*）。

   您應該會看到下列命令視窗：

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. [**選擇即時偵錯工具**] 對話方塊隨即開啟。

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   在 [**可用的調試**程式] 底下，選取 [**新的 \<your preferred Visual Studio version/edition> 實例**] （如果尚未選取）。

1. 選取 [確定]。

   ThrowsNullException 專案會在 Visual Studio 的新實例中開啟，並在擲回例外狀況的那一行停止執行：

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

此時您可以開始進行調試。 如果您正在對實際的應用程式進行偵測，就必須找出程式碼擲回例外狀況的原因。

> [!CAUTION]
> 如果您的應用程式包含不受信任的程式碼，就會出現安全性警告對話方塊，讓您決定是否要繼續進行偵錯工具。 在您繼續進行偵錯工具之前，請先決定您是否信任該程式碼。 這是您自行撰寫的程式碼嗎？ 如果應用程式在遠端電腦上執行，您認得它的處理序名稱嗎？ 如果應用程式是在本機執行，請考慮在您的電腦上執行惡意程式碼的可能性。 如果您決定程式碼可信任，請選取 **[確定]**。 否則，請選取 [取消]****。

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a>對即時調試進行疑難排解

如果應用程式損毀時不會啟動即時偵測，即使已在 Visual Studio 中啟用：

- Windows 錯誤報告可能會接管電腦上的錯誤處理。

  若要修正此問題，請使用註冊表**編輯器，將****值資料**為**1**的**DWORD 值**新增至下列登錄機碼：

  - **HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\Windows 錯誤報告**

  - （適用于64位機器）： **HKEY_LOCAL_MACHINE \Software\wow6432node\microsoft\windows\windows 錯誤報表**

  如需詳細資訊，請參閱[。WER 設定](/windows/desktop/wer/wer-settings)。

- 已知的 Windows 問題可能會使即時偵錯工具失敗。

  修正方法是將**值資料**為**1**的**自動** **DWORD 值**新增至下列登錄機碼：

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - （適用于64位電腦）： **HKEY_LOCAL_MACHINE \Software\wow6432node\microsoft\windows NT\CurrentVersion\AeDebug**

您可能會在即時的調試過程中看到下列錯誤訊息：

- **無法附加至損毀進程。指定的程式不是 Windows 或 MS-DOS 程式。**

    偵錯工具嘗試附加至在另一個使用者之下執行的進程。

    若要解決這個問題，請在 Visual Studio 中，開啟 [ **Debug**  >  **Attach to Process**]，然後在 [**可使用的進程**] 清單中尋找您要進行偵錯工具的進程。 如果您不知道進程的名稱，請在 [ **Visual Studio 即時偵錯工具**] 對話方塊中尋找處理序識別碼。 在 [**可使用的進程**] 清單中選取進程，然後選取 [**附加**]。 選取 [**否**] 以關閉即時偵錯工具對話方塊。

- **由於沒有使用者登入，無法啟動偵錯工具。**

    沒有任何使用者登入主控台，因此沒有任何使用者會話可以顯示即時調試對話。

    若要修正這個問題，請登入該電腦。

- **類別未登錄。**

    偵錯工具嘗試建立未註冊的 COM 類別，可能是因為安裝問題所致。

    若要修正此問題，請使用 Visual Studio 安裝程式來重新安裝或修復您的 Visual Studio 安裝。

## <a name="see-also"></a>另請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [選項、調試功能、即時對話方塊](../debugger/just-in-time-debugging-options-dialog-box.md)
- [安全性警告附加至不受信任的使用者所擁有的處理序可能會造成危險。如果下面的資訊看起來有問題，或者您並不確定，請不要附加至此處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
