---
title: Visual Studio 中的診斷資料配接器逾時 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Diagnostic Data Adapter, increasing time-outs
ms.assetid: 39fff4fc-9233-4f67-96ac-e81bbaf7ca82
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 50bdf23e83ca9ef70c40b010050a3e6aba90e0a5
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-prevent-time-outs-for-diagnostic-data-adapters"></a>如何：防止診斷資料配接器逾時

如果您在測試設定中使用診斷資料配接器，當您啟動測試回合時，可能會由於下列其中一個原因而發生逾時：

-   測試控制器服務並未在測試控制器電腦上執行。 您可能必須重新啟動服務。 如需如何判斷測試控制器和管理測試控制器的詳細資訊，請參閱[使用 Visual Studio 管理測試控制器和測試代理程式](../test/manage-test-controllers-and-test-agents.md)。

-   如果您在遠端電腦上收集資料，防火牆可能會封鎖 Microsoft Test Manager。 執行 Microsoft Test Manager 的電腦必須接受來自測試控制器的連入連線。 當 Microsoft Test Manager 沒有收到來自控制器的訊息 (因為防火牆封鎖了訊息) 時，就會發生逾時。 您必須在執行 Microsoft Test Manager 的電腦上檢查防火牆設定。 如需防火牆設定的詳細資訊，請參閱下列 [Microsoft 網站](http://go.microsoft.com/fwlink/?LinkId=184980)。

-   測試控制器無法解析執行 Microsoft Test Manager 之電腦的名稱。 如果 DNS 提供了錯誤的位址給這部電腦，就可能會發生這種情況。 您可能必須連絡網路系統管理員來解決此問題。

 當您執行必須收集大量資料的長時間測試時，可能會發現這項資料的收集作業逾時。您可以使用下列程序來解決此問題。

 您可以更新 Microsoft Test Manager 的組態檔或發生逾時之測試代理程式的組態檔來增加逾時值。

 Microsoft Test Manager 的組態檔稱為 **mtm.exe.config**。所在目錄為 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*。

 若要更新測試代理程式，則需更新測試代理程式電腦上的下列組態檔。 這些檔案都位於測試代理程式電腦的相同目錄 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* 中。

-   QTAgent.exe.config

-   QTAgent32.exe.config

-   QTDCAgent.exe.config

-   QTDCAgent32.exe.config

 如果您執行手動測試並且從環境中收集資料，當系統建立 Bug 或完成測試案例時，診斷資料配接器已經收集的任何資料都會傳輸至執行手動測試的電腦。 如果您已經收集大量資料或者網路連線速度很慢，所花費的時間可能會超過預設值 60 秒。 例如，如果您已經將 IntelliTrace 配接器設定為收集許多處理序的 IntelliTrace 事件和呼叫資訊，這項資料的傳輸可能會超過預設逾時。若要增加這個值，您可以使用下列程序來更新 **mtm.exe.config**。

 如果測試執行器活動發生逾時或測試代理程式發生逾時，則會顯示錯誤訊息。在測試代理程式的錯誤訊息中，包含發生逾時之測試代理程式電腦的相關資訊。請根據您收到的錯誤訊息，利用下列程序更新組態檔。

## <a name="to-increase-the-time-outs-for-your-diagnostic-data-adapters"></a>若要為您的診斷資料配接器增加逾時

1.  開啟 [Windows 檔案總管] (或 [檔案總管]) 視窗。

     若要執行這個步驟，請以滑鼠右鍵按一下 [開始]，然後指向 [檔案總管]。

    > [!NOTE]
    > 您可能需要系統管理員權限，才能更新檔案。

2.  在電腦上找到 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* 目錄，其中包含您必須更新的檔案。

3.  以滑鼠右鍵按一下檔案，然後指向 [開啟檔案]。 選取一個編輯器。

     檔案隨即顯示在該編輯器中。 此檔案中儲存了許多設定， 大部分設定都能使用 Microsoft Test Manager 加以變更。 不過，逾時設定必須依照下列步驟所述，以手動方式變更。

4.  您必須修改測試執行設定區段，增加逾時值。 本區段具有下列格式：

    ```
    <!-- Begin: Test execution settings -->

        <!-- How long test runner will wait for an event raised to all local data collectors to complete.  Default is 300. -->
        <add key="DataCollectorEventTimeoutInSeconds" value="300"/>

        <!-- How long test runner will wait for test run operations, such as starting or stopping a test run, to complete.  Default is 60. -->
        <add key="RunOperationTimeoutInSeconds" value="60"/>

        <!-- End: Test execution settings -->
    ```

5.  若要增加診斷資料配接器等候事件完成的等待時間，請增加 **DataCollectorEventTimeoutInSeconds** 機碼的值。

6.  如果逾時錯誤訊息是因為測試執行器活動而產生，您必須增加 **RunOperationTimeoutInSeconds** 機碼的值。

7.  若要增加將針對 Bug 或測試結束時所收集的任何資料傳輸至執行測試之電腦的逾時值，您必須將下列逾時新增至檔案 appSettings 區段中的 **mtm.exe.config**：

    ```
    <!-- How long test runner waits for data collected by diagnostic data adapters to be transferred to the computer. Default is 60 seconds. -->
    <add key="GetCollectorDataTimeout" value="300"/>
    ```

    > [!NOTE]
    > 逾時值是以秒為單位。

8.  儲存對檔案進行的變更，然後重新執行先前逾時的測試。

## <a name="see-also"></a>另請參閱

- [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)