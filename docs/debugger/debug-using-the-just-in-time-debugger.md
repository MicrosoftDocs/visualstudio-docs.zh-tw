---
title: 使用 Just-In-Time 偵錯工具進行偵錯 |Microsoft Docs
ms.date: 09/24/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2aff8e1b515f460e6fdc31a528e6730971b7853
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62853229"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>在 Visual Studio 中使用 Just-In-Time 偵錯工具進行偵錯

在 Just-in-time 偵錯可以 Visual Studio 會自動啟動時執行外部的 Visual Studio 錯誤或損毀的應用程式。 只要時間偵錯，您可以測試 Visual Studio 中，外部應用程式與開啟 Visual Studio 開始偵錯發生問題時。

在 Just-in-time 偵錯適用於 Windows 桌面應用程式。 它不適用於通用 Windows 應用程式，或裝載於原生應用程式，例如視覺化檢視中的 managed 程式碼。

> [!TIP]
> 如果您只想要停止 [Just-In-Time 偵錯工具] 對話方塊中，不會出現，但不安裝 Visual studio，請參閱[停用 Just-In-Time 偵錯工具](../debugger/just-in-time-debugging-in-visual-studio.md)。 如果您一次安裝 Visual Studio，您可能需要[停用 Just In Time 偵錯從 Windows 登錄](#disable-just-in-time-debugging-from-the-windows-registry)。

## <a name="BKMK_Enabling"></a> 啟用或停用 Just In Time Visual Studio 偵錯

>[!NOTE]
>若要啟用或停用 Just 時間偵錯，您必須執行 Visual Studio 系統管理員身分。 啟用或停用 Just In Time 偵錯設定登錄機碼，並可能需要系統管理員權限，才能變更該金鑰。 若要開啟 Visual Studio 以系統管理員，以滑鼠右鍵按一下 Visual Studio 應用程式，然後選擇**系統管理員身分執行**。

您可以設定只需的時間從 Visual Studio 偵錯**工具** > **選項**(或**偵錯** > **選項**) 對話方塊。

**啟用或停用 Just-In-Time 偵錯：**

1. 在 **工具**或是**偵錯**功能表上，選取**選項** > **偵錯** >  **在 Just-in-time**。

   ![啟用或停用 JIT 偵錯](../debugger/media/dbg-jit-enable-or-disable.png "啟用或停用 JIT 偵錯")

1. 在 **啟用的 Just-In-Time 偵錯這些程式碼類型的**方塊中，選取您想要只需時間偵錯來偵錯的程式碼類型：**受控**，**原生**，和/或**指令碼**。

1. 選取 [確定]。

如果您啟用的時間只需偵錯工具，但它未開啟時的應用程式當機或錯誤，請參閱[疑難排解 Just-In-Time 偵錯](#jit_errors)。

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>停用 Just 時間偵錯從 Windows 登錄

即使電腦上已沒有安裝 Visual Studio，Just-In-Time 偵錯可能仍然為啟用狀態。 如果不會再安裝 Visual Studio，您可以停用 Just 時間透過編輯 Windows 登錄偵錯。

**藉由編輯登錄來停用 Just-In-Time 偵錯：**

1. 從 Windows**開始**功能表中，執行**登錄編輯器**(*regedit.exe*)。

2. 在 [**登錄編輯程式**] 視窗中，找出並刪除下列登錄項目：

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![登錄機碼 JIT](../debugger/media/dbg-jit-registry.png "JIT 登錄機碼")

3. 如果您的電腦執行 64 位元作業系統，也會刪除下列登錄項目：

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    請務必不要刪除或變更任何其他的登錄機碼。

5. 關閉**登錄編輯程式**視窗。

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>啟用 Just In Time Windows Form 的偵錯

根據預設，Windows Form 應用程式會有最上層的例外狀況處理常式，可讓應用程式能夠復原時繼續執行。 如果您的 Windows Forms 應用程式會擲回未處理的例外狀況，它會顯示下列對話方塊：

![Windows 表單未處理例外狀況](../debugger/media/windowsformsunhandledexception.png "Windows 表單未處理例外狀況")

若要啟用 Just-in-time 時間偵錯，而不標準的 Windows 表單錯誤處理，請新增這些設定：

- 在 `system.windows.forms`一節*machine.config*或*\<應用程式名稱 >。 .exe.config*檔案中，設定`jitDebugging`值`true`:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- 在C++Windows Form 應用程式，也會設定`DebuggableAttribute`要`true`中 *.config*檔案或程式碼中。 如果您使用 [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) 而且未使用 [/Og](/cpp/build/reference/og-global-optimizations) 進行編譯，則編譯器將會設定這個屬性 (Attribute)。 如果您想要偵錯非最佳化的發行組建，不過，您必須設定`DebuggableAttribute`藉由在您的應用程式中加入下列這一行*AssemblyInfo.cpp*檔案：

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   如需詳細資訊，請參閱<xref:System.Diagnostics.DebuggableAttribute>。

## <a name="BKMK_Using_JIT"></a>使用 Just In Time 偵錯
此範例會引導您只要時間偵錯時應用程式擲回錯誤。

- 您必須遵循下列步驟安裝的 Visual Studio。 如果您沒有 Visual Studio，您可以下載免費[Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)。

- 請確定 Just In Time 偵錯[啟用](#BKMK_Enabling)中**工具** > **選項** > **偵錯** > **-Just-in-time**。

針對此範例中，您將建立C#會擲回的 Visual Studio 中的主控台應用程式[NullReferenceException](/dotnet/api/system.nullreferenceexception)。

1. 在 Visual Studio 中建立C#主控台應用程式 (**檔案** > **新增** > **專案** > **Visual C#**   > **主控台應用程式**) 名為*ThrowsNullException*。 如需在 Visual Studio 中建立專案的詳細資訊，請參閱[逐步解說：建立簡單的應用程式](/visualstudio/get-started/csharp/tutorial-wpf)。

1. 當專案開啟時 Visual Studio 中時，開啟*Program.cs*檔案。 取代為下列程式碼，這會列印到主控台一行，然後擲回 NullReferenceException 的 main （） 方法：

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. 若要建置方案時，選擇**偵錯**（預設值） 或**Release**組態，然後選取**建置** > **重建方案**.

   > [!NOTE]
   > - 選擇**偵錯**設定完整的偵錯體驗。
   > - 如果您選取[Release](../debugger/how-to-set-debug-and-release-configurations.md)組態，您必須關閉[Just My Code](../debugger/just-my-code.md)運作此程序。 底下**工具** > **選項** > **偵錯**，取消選取**啟用 Just My Code**。

   如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。

1. 開啟 建置的應用程式*ThrowsNullException.exe*中您C#專案資料夾 (*...\ThrowsNullException\ThrowsNullException\bin\Debug*或是 *...\ThrowsNullException\ThrowsNullException\bin\Release*)。

   您應該會看到下列的 [命令] 視窗：

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. **選擇 Just-In-Time 偵錯工具** 對話方塊隨即開啟。

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   底下**可用的偵錯工具**，選取**的新執行個體\<您慣用 Visual Studio 版本 >**，如果尚未選取。

1. 選取 [確定]。

   在擲回例外狀況的行已停止執行，在 Visual Studio 中的新執行個體中開啟 ThrowsNullException 專案：

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

您可以開始在此時偵錯。 如果您已將實際的應用程式偵錯，您必須了解為什麼程式碼會擲回例外狀況。

> [!CAUTION]
> 如果您的應用程式包含不受信任的程式碼，會出現安全性警告對話方塊，讓您決定是否要繼續進行偵錯。 繼續偵錯，請先決定您是否信任的程式碼。 這是您自行撰寫的程式碼嗎？ 如果應用程式在遠端電腦上執行，您認得它的處理序名稱嗎？ 如果在本機執行應用程式，請考慮在您的電腦上執行的惡意程式碼的可能性。 如果您決定是值得信任的程式碼，請選取**確定**。 否則，請選取 [取消]。

## <a name="jit_errors"></a> 疑難排解 Just In Time 偵錯

如果 Just In Time 偵錯不啟動應用程式當機，即使它在 Visual Studio 中啟用：

- Windows 錯誤報告可以接管您的電腦上處理的錯誤。

  若要修正此問題，請使用登錄編輯器，將**DWORD 值**的**停用**，使用**數值資料**的**1**，下列的登錄機碼：

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows 錯誤報告**

  - （適用於 64 位元電腦）：**HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  如需詳細資訊，請參閱[。WER 設定](https://docs.microsoft.com/windows/desktop/wer/wer-settings)。

- 已知的 Windows 問題造成的時間就失敗的偵錯工具。

  修正方法是新增**DWORD 值**的**自動**，使用**數值資料**的**1**，下列的登錄機碼：

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - （適用於 64 位元電腦）：**HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

您可能會看到下列錯誤訊息在 Just In Time 期間偵錯：

- **無法附加至沒有回應的處理序。所指定的程式不是 Windows 或 MS-DOS 程式。**

    偵錯工具會嘗試將附加至在另一位使用者執行的程序。

    若要解決這個問題，請在 Visual Studio 中，開啟**偵錯** > **připojit k procesu**，並尋找您要在偵錯的處理序**可用的處理序**清單。 如果您不知道處理序的名稱，找到處理序識別碼中**Visual Studio Just-In-Time 偵錯工具**對話方塊。 選取中的程序**可用的處理序**清單，然後選取**附加**。 選取 [ **No**關閉的時間只需偵錯工具] 對話方塊。

- **由於沒有使用者登入，無法啟動偵錯工具。**

    沒有登入主控台，因此沒有要顯示的時間就沒有任何使用者工作階段的使用者偵錯 對話方塊。

    若要修正這個問題，請登入該電腦。

- **類別未登錄。**

    偵錯工具會嘗試建立的 COM 類別未註冊，可能因為未安裝的問題。

    若要修正此問題，請重新安裝或修復您安裝 Visual Studio 中使用 Visual Studio 安裝程式。

## <a name="see-also"></a>另請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [選項、 偵錯，Just In Time 對話方塊](../debugger/just-in-time-debugging-options-dialog-box.md)
- [安全性警告：附加至未受信任的使用者所擁有的處理序可能會造成危險。如果下面的資訊看起來有問題，或者您並不確定，請不要附加至此處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
