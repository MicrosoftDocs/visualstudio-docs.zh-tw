---
title: 在 Visual Studio 中 SharePoint 工具的偵錯擴充功能 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f838363b52a85faff022f49542fcc2fcc7e450d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950812"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>偵錯在 Visual Studio 中 SharePoint 工具擴充功能
  您可以偵錯的實驗執行個體或一般的執行個體的 Visual Studio 中 SharePoint 工具擴充功能。 如果您需要的行為延伸模組進行疑難排解，您也可以修改登錄值以顯示其他錯誤資訊，並設定 Visual Studio 執行 SharePoint 命令的方式。

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>偵錯 Visual Studio 的實驗執行個體中的延伸模組
 為了保護您的 Visual Studio 開發環境，從意外損毀，方法為未經測試的延伸模組，Visual Studio SDK 提供替代的 Visual Studio 執行個體，稱為*實驗執行個體*，您可以使用若要安裝並測試擴充功能。 使用一般的執行個體的 Visual Studio，開發新的擴充功能，但您偵錯，並在實驗執行個體上執行。 如需詳細資訊，請參閱 <<c0> [ 實驗的執行個體](../extensibility/the-experimental-instance.md)。

 如果您使用 VSIX 專案來部署您的延伸模組和 VSIX 專案是啟始專案方案中的，Visual Studio 自動安裝，並在實驗執行個體中執行此延伸模組，當您偵錯您的解決方案。 啟始專案是專案啟動偵錯包含多個專案的方案時執行。 如需使用 VSIX 專案部署您的擴充功能的詳細資訊，請參閱[部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

 如需示範如何偵錯各種類型的 Visual Studio 的實驗執行個體中的延伸模組的範例，請參閱下列逐步解說：

-   [逐步解說：擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

-   [逐步解說：使用項目範本，第 1 部分中建立自訂動作專案項目](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

-   [逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

-   [逐步解說：擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

-   [逐步解說：呼叫 SharePoint 用戶端物件模型，在 伺服器總管延伸模組](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>偵錯 Visual Studio 的一般執行個體中的延伸模組
 如果您想要偵錯擴充功能專案的 Visual Studio 一般的執行個體中，第一次規則執行個體中安裝擴充功能。 然後，將偵錯工具附加至第二個 Visual Studio 處理序。 完成之後，您就可以移除擴充功能，使它不會再載入在開發電腦上。

#### <a name="to-install-the-extension"></a>安裝擴充功能

1.  關閉所有 Visual Studio 執行個體。

2.  在 擴充功能專案的組建輸出資料夾，開啟 *.vsix*檔案按兩下，或開啟其捷徑功能表，然後選擇**開啟**:

3.  在 [ **Visual Studio 擴充功能安裝程式**對話方塊方塊中，選擇您想要安裝擴充功能，再選擇的 Visual Studio 版本**安裝**] 按鈕。

     Visual Studio 會延伸檔案安裝至 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*作者姓名*\\*副檔名*\\*版本*。 此路徑中的最後三個資料夾，建構自`Author`， `Name`，並`Version`中的項目*extension.vsixmanifest*的延伸模組檔案。

4.  Visual Studio 安裝擴充功能之後，請選擇**關閉** 按鈕。

#### <a name="to-debug-the-extension"></a>若要偵錯擴充功能

1.  以系統管理員權限啟動 Visual Studio，然後開啟 擴充功能專案。 下列的步驟，請參閱 Visual studio 這個執行個體*第一次執行個體*。

2.  系統管理員權限啟動 Visual studio 的另一個執行個體。 下列的步驟，請參閱 Visual studio 這個執行個體*第二個執行個體*。

3.  切換至 Visual Studio 的第一個執行個體。

4.  在功能表列上選擇 **偵錯**，**附加至處理序**。

5.  在 **可用的處理序**清單中，選擇*devenv.exe*。 此項目是指 Visual Studio; 第二個執行個體這是您想要偵錯您的專案延伸模組的執行個體。

6.  選擇**附加** 按鈕。

     Visual Studio 偵錯模式中執行擴充功能專案。

7.  切換至 Visual Studio 的第二個執行個體。

8.  建立新的 SharePoint 專案，以載入您的延伸模組。 例如，如果您正在偵錯擴充功能的清單定義專案項目，建立**清單定義**專案。

9. 執行任何步驟都必須測試延伸模組程式碼。

10. 當您完成偵錯延伸模組，請關閉 Visual Studio 的第二個執行個體。

#### <a name="to-remove-the-extension"></a>移除擴充功能

1.  在 Visual Studio 中，在功能表列上選擇**工具**，**擴充功能和更新**。

     [擴充功能和更新] 對話方塊隨即開啟。

2.  在延伸模組清單中，選擇的延伸模組的名稱，然後選擇**解除安裝** 按鈕。

3.  在出現的對話方塊中，選擇**是**按鈕，以確認您想要解除安裝擴充功能。

4.  選擇**立即重新啟動**按鈕以完成解除安裝。

## <a name="debug-sharepoint-commands"></a>偵錯 SharePoint 命令
 如果您想要偵錯組件的 SharePoint 工具擴充功能的 SharePoint 命令，您必須將偵錯工具附加*vssphost4.exe*程序。 這是 64 位元主控件程序來執行 SharePoint 命令。 如需有關 SharePoint 命令和*vssphost4.exe*，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>若要將偵錯工具附加至 vssphost4.exe 處理序

1.  開始偵錯您的 Visual Studio 實驗執行個體或一般執行個體中的 Visual Studio 的擴充功能，依照上述指示。

2.  在 Visual Studio 中您正在偵錯工具，在功能表列的執行個體，選擇**偵錯**，**附加至處理序**。

3.  在 **可用的處理序**清單中，選擇*vssphost.exe*。

    > [!NOTE]
    >  如果 vssphost.exe 不會出現在清單中，您必須啟動*vssphost4.exe*程序，在您執行擴充功能的 Visual Studio 執行個體。 一般而言，您可以執行某個動作而造成 Visual Studio 來連線至 SharePoint 網站，在開發電腦上。 比方說，Visual Studio 會啟動*vssphost4.exe*當您展開站台的連線節點 （節點會顯示網站 URL） 底下**SharePoint 連線**中的節點**伺服器總管**視窗中，或當您新增特定 SharePoint 專案項目，例如**清單執行個體**或是**事件接收器**至 SharePoint 專案項目。

4.  選擇**附加** 按鈕。

5.  在 Visual Studio 進行偵錯的執行個體，執行步驟，才能執行您的命令。

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>修改登錄值，以協助偵錯 SharePoint 工具擴充功能
 當您偵錯的 Visual Studio 中 SharePoint 工具擴充功能時，您可以修改登錄，以協助您疑難排解擴充功能中的值。 值存在底下**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**索引鍵。 依預設沒有這些值。

 為了協助疑難排解 SharePoint 工具的任何延伸模組，您可以建立並設定 EnableDiagnostics 值。 下表描述此值。

|值|描述|
|-----------|-----------------|
|EnableDiagnostics|指定是否要將診斷訊息顯示在的 REG_DWORD**輸出**視窗。<br /><br /> 顯示診斷訊息，請將此值設定為 1。 若要停止顯示訊息，將此值設定為 0，或刪除此值。<br /><br /> 若要將訊息寫入至**輸出**視窗從 SharePoint 工具擴充功能，請使用 SharePoint 專案服務。 如需詳細資訊，請參閱 <<c0> [ 使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。|

 如果您的延伸模組包含 SharePoint 命令，您可以建立並設定其他值，以協助疑難排解命令。 下表描述這些值。

|值|描述|
|-----------|-----------------|
|AttachDebuggerToHostProcess|指定是否要顯示對話方塊，可讓您附加偵錯工具的 REG_DWORD *vssphost4.exe*只要它啟動。 這只有在啟動之後，立即 vssphost.exe 執行的命令，您要偵錯時相當實用，但沒有足夠的時間來執行命令之前，以手動方式附加偵錯工具。 若要顯示對話方塊中， *vssphost4.exe*呼叫<xref:System.Diagnostics.Debugger.Break%2A>啟動時的方法。<br /><br /> 啟用此行為，請將此值設定為 1。 若要關閉此行為，將此值設定為 0，或刪除此值。<br /><br /> 如果您設定此值為 1 時，您也可以讓您有足夠的時間來附加偵錯工具，Visual Studio 預期之前 HostProcessStartupTimeout 值增加*vssphost4.exe*來表示成功啟動。|
|ChannelOperationTimeout|指定的時間 （秒），Visual Studio，等候執行 SharePoint 命令的 REG_DWORD。 如果命令不會執行的時間，<xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>就會擲回。<br /><br /> 預設值是 120 秒。|
|HostProcessStartupTimeout|指定時間，以秒為單位的 REG_DWORD，Visual Studio 會等到*vssphost4.exe*來表示成功啟動。 如果*vssphost4.exe*不會不發出訊號成功的開始時間，<xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>就會擲回。<br /><br /> 預設值為 60 秒。|
|MaxReceivedMessageSize|指定允許的大小，以位元組為單位，Visual Studio 之間傳遞的 WCF 訊息的最大的 REG_DWORD 並*vssphost4.exe*。<br /><br /> 預設值為 1048576 個位元組 (1 MB)。|
|MaxStringContentLength|指定允許的大小，以位元組為單位，Visual Studio 之間傳遞的字串的最大的 REG_DWORD 並*vssphost4.exe*。<br /><br /> 預設值為 1048576 個位元組 (1 MB)。|

## <a name="see-also"></a>另請參閱

- [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
