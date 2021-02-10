---
title: Visual Studio 中 SharePoint 工具的偵錯工具擴充功能 |Microsoft Docs
description: Visual Studio 中 SharePoint 工具的 Debug 擴充功能。 在實驗性實例或一般的 VS 實例中，偵錯工具的 SharePoint 工具延伸模組。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2b098ac007825745e13481592760be9d2badeb55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948904"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio 中 SharePoint 工具的 Debug 擴充功能
  您可以在實驗實例或 Visual Studio 的一般實例中，進行 SharePoint 工具擴充功能的偵錯工具。 如果您需要針對延伸模組的行為進行疑難排解，您也可以修改登錄值以顯示其他錯誤資訊，以及設定 Visual Studio 執行 SharePoint 命令的方式。

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Visual Studio 的實驗性實例中的 Debug 擴充功能
 為了保護您的 Visual Studio 開發環境免于未經過測試的延伸模組遭到意外損毀，Visual Studio SDK 提供替代的 Visual Studio 實例，稱為 *實驗實例*，可供您用來安裝和測試擴充功能。 您可以使用 Visual Studio 的一般實例來開發新的擴充功能，但您會在實驗實例中進行調試和執行。 如需詳細資訊，請參閱 [實驗實例](../extensibility/the-experimental-instance.md)。

 如果您使用 VSIX 專案來部署您的延伸模組，而 VSIX 專案是方案中的啟始專案，Visual Studio 在您將解決方案進行偵錯工具時，會自動在實驗實例中安裝並執行延伸模組。 啟始專案是當您對包含多個專案的方案進行程式的偵測時，所啟動的專案。 如需使用 VSIX 專案部署擴充功能的詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

 如需示範如何在 Visual Studio 的實驗實例中，為各種類型的延伸進行偵錯工具的範例，請參閱下列逐步解說：

- [逐步解說：擴充 SharePoint 專案專案類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [逐步解說：在伺服器總管擴充功能中呼叫 SharePoint 用戶端物件模型](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Visual Studio 的一般實例中的 Debug 擴充功能
 如果您想要在 Visual Studio 的一般實例中，對擴充功能專案進行偵錯工具，請先在一般實例中安裝延伸模組。 然後，將偵錯工具附加至第二個 Visual Studio 進程。 完成之後，您可以移除此延伸模組，使其不再于開發電腦上載入。

#### <a name="to-install-the-extension"></a>安裝擴充功能

1. 關閉所有 Visual Studio 執行個體。

2. 在擴充功能專案的 [組建輸出] 資料夾中，按兩下 *.vsix* 檔案，或開啟其快捷方式功能表，然後選擇 [ **開啟**]：

3. 在 [ **Visual Studio 擴充功能安裝程式** ] 對話方塊中，選擇您要安裝擴充功能的 Visual Studio 版本，然後選擇 [ **安裝** ] 按鈕。

     Visual Studio 將擴充檔安裝至%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions \\ *作者名稱* \\ *延伸模組名稱* \\ *版本*。 這個路徑中的最後三個資料夾是由擴充功能的 extension.vsixmanifest 檔案中的、和專案所構成 `Author` `Name` `Version` 。 

4. Visual Studio 安裝延伸模組之後，請選擇 [ **關閉** ] 按鈕。

#### <a name="to-debug-the-extension"></a>若要 debug 擴充功能

1. 以系統管理員許可權開啟 Visual Studio，然後開啟擴充功能專案。 下列步驟會將 Visual Studio 的實例參考為 *第一個實例*。

2. 以系統管理員許可權啟動 Visual Studio 的另一個實例。 下列步驟會將 Visual Studio 的實例參考為 *第二個實例*。

3. 切換至 Visual Studio 的第一個實例。

4. 在功能表列上，選擇 [ **Debug**]、[ **附加至進程**]。

5. 在 [ **可使用的進程** ] 清單中，選擇 [ *devenv.exe*]。 此專案是指 Visual Studio 的第二個實例;這是您想要在其中將專案延伸模組進行偵錯工具的實例。

6. 選擇 [ **附加** ] 按鈕。

     Visual Studio 在「偵測模式」中執行延伸模組專案。

7. 切換至 Visual Studio 的第二個實例。

8. 建立新的 SharePoint 專案以載入您的延伸模組。 例如，如果您正在針對清單定義專案專案的擴充功能進行偵錯工具，請建立 **清單定義** 專案。

9. 執行測試擴充程式碼所需的任何步驟。

10. 當您完成擴充功能的偵錯工具時，請關閉 Visual Studio 的第二個實例。

#### <a name="to-remove-the-extension"></a>移除擴充功能

1. 在 Visual Studio 的功能表列上，選擇 [ **工具**]、[ **擴充功能和更新**]。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在擴充功能清單中，選擇延伸模組的名稱，然後選擇 [ **卸載** ] 按鈕。

3. 在出現的對話方塊中，選擇 [ **是** ] 按鈕，確認您想要卸載延伸模組。

4. 選擇 [ **立即重新開機** ] 按鈕以完成卸載。

## <a name="debug-sharepoint-commands"></a>調試 SharePoint 命令
 如果您想要針對 SharePoint 工具延伸模組的一部分來進行 SharePoint 命令的偵錯工具，您必須將偵錯工具附加至 *vssphost4.exe* 進程。 這是執行 SharePoint 命令的64位主機進程。 如需有關 SharePoint 命令和 *vssphost4.exe* 的詳細資訊，請參閱 [呼叫 sharepoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>將偵錯工具附加至 vssphost4.exe 進程

1. 遵循上述指示，開始在 Visual Studio 的實驗性實例中，或 Visual Studio 的一般實例中，啟動偵錯工具。

2. 在您執行偵錯工具的 Visual Studio 實例中，選擇功能表列上的 [ **Debug**]、[ **附加至進程**]。

3. 在 [ **可使用的進程** ] 清單中，選擇 [ *vssphost.exe*]。

    > [!NOTE]
    > 如果 vssphost.exe 未出現在清單中，您必須在執行擴充功能的 Visual Studio 實例中啟動 *vssphost4.exe* 處理常式。 一般來說，您可以執行動作，讓 Visual Studio 連接到開發電腦上的 SharePoint 網站。 例如，當 (您在 [**伺服器總管**] 視窗的 [ **sharepoint 連接**] 節點下顯示網站 URL) 的節點，或將某些 sharepoint 專案專案（例如 **清單實例** 或 **事件接收器** 專案）加入至 SharePoint 專案時，Visual Studio 開始 *vssphost4.exe* 。

4. 選擇 [ **附加** ] 按鈕。

5. 在正在進行調試的 Visual Studio 實例中，執行執行命令所需的步驟。

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>修改登錄值以協助調試 SharePoint 工具延伸模組
 當您在 Visual Studio 中進行 SharePoint 工具的擴充功能的偵錯工具時，您可以修改登錄中的值，以協助您疑難排解擴充功能。 值存在於 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** 索引鍵下。 這些值預設不存在。

 若要協助疑難排解 SharePoint 工具的任何擴充功能，您可以建立並設定 EnableDiagnostics 值。 下表描述此值。

|值|描述|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD，指定是否要在 [ **輸出** ] 視窗中顯示診斷訊息。<br /><br /> 若要顯示診斷訊息，請將此值設定為1。 若要停止顯示訊息，請將此值設定為0，或刪除此值。<br /><br /> 若要從 SharePoint 工具延伸模組將訊息寫入至 [ **輸出** ] 視窗，請使用 sharepoint 專案服務。 如需詳細資訊，請參閱 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。|

 如果您的延伸模組包含 SharePoint 命令，您可以建立並設定其他值，以協助疑難排解命令。 下表描述這些值。

|值|描述|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD，指定是否要顯示對話方塊，讓您在偵錯工具啟動時，立即將偵錯工具附加至 *vssphost4.exe* 。 如果您想要 debug 的命令是在啟動後立即 vssphost.exe 執行，而且沒有足夠的時間在執行命令之前手動附加偵錯工具，這就很有用。 若要顯示對話方塊， *vssphost4.exe* <xref:System.Diagnostics.Debugger.Break%2A> 會在啟動時呼叫方法。<br /><br /> 若要啟用此行為，請將此值設定為1。 若要關閉此行為，請將此值設定為0，或刪除此值。<br /><br /> 如果您將此值設定為1，您可能也會想要增加 HostProcessStartupTimeout 值，以提供足夠的時間來附加偵錯工具，Visual Studio 預期 *vssphost4.exe* 告知它已順利啟動。|
|ChannelOperationTimeout|REG_DWORD，指定 Visual Studio 等候 SharePoint 命令執行的時間（以秒為單位）。 如果命令未及時執行，則會擲回 <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> 。<br /><br /> 預設值是 120 秒。|
|HostProcessStartupTimeout|REG_DWORD，指定 Visual Studio 等候 *vssphost4.exe* 成功啟動的時間（以秒為單位）。 如果 *vssphost4.exe* 沒有通知成功的開始時間， <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> 就會擲回。<br /><br /> 預設值是 60 秒。|
|MaxReceivedMessageSize|REG_DWORD，指定 Visual Studio 和 *vssphost4.exe* 之間傳遞之 WCF 訊息的最大允許大小（以位元組為單位）。<br /><br /> 預設值為1048576個位元組 (1 MB) 。|
|MaxStringContentLength|REG_DWORD，指定 Visual Studio 和 *vssphost4.exe* 之間傳遞之字串的最大允許大小（以位元組為單位）。<br /><br /> 預設值為1048576個位元組 (1 MB) 。|

## <a name="see-also"></a>另請參閱

- [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [在 Visual Studio 中部署 SharePoint 工具的延伸模組](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
