---
title: "在 Visual Studio 中 SharePoint 工具的偵錯擴充功能 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, debugging extensions
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98bb43322d4a222d63bafac22d78e433a3000530
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-extensions-for-the-sharepoint-tools-in-visual-studio"></a>偵錯 Visual Studio 中 SharePoint 工具的擴充功能
  您可以偵錯在實驗執行個體或規則的執行個體的 Visual Studio 中 SharePoint 工具擴充功能。 如果您需要疑難排解延伸模組的行為，您也可以修改登錄值以顯示其他錯誤資訊，並設定 Visual Studio 如何執行 SharePoint 命令。  
  
## <a name="debugging-extensions-in-the-experimental-instance-of-visual-studio"></a>在 Visual Studio 的實驗執行個體中的偵錯擴充功能  
 未經測試的延伸模組所保護的意外損毀 Visual Studio 開發環境，Visual Studio SDK 提供替代的 Visual Studio 執行個體，稱為*實驗執行個體*，可讓您安裝及測試擴充功能。 使用規則的執行個體的 Visual Studio，開發新的延伸模組，但偵錯，並在實驗執行個體中加以執行。 如需詳細資訊，請參閱[實驗執行個體的](/visualstudio/extensibility/the-experimental-instance)。  
  
 如果您使用 VSIX 專案來部署您的擴充功能，而且此 VSIX 專案中方案的啟始專案，Visual Studio 自動安裝，並實驗執行個體中執行擴充功能，當您偵錯您的方案。 啟動專案為專案啟動偵錯包含多個專案的方案時。 如需使用來部署您的擴充功能的 VSIX 專案的詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  

 如需示範如何偵錯 Visual Studio 的實驗執行個體中延伸模組的各種類型的範例，請參閱下列逐步解說：  
  
-   [逐步解說：擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [逐步解說：使用項目範本建立自訂動作專案項目 (第 1 部分)](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [逐步解說：擴充伺服器總管以顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [逐步解說：在伺服器總管延伸模組中呼叫 SharePoint 用戶端物件模型](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## <a name="debugging-extensions-in-the-regular-instance-of-visual-studio"></a>規則的執行個體的 Visual Studio 中偵錯擴充功能  
 如果您想要偵錯擴充功能專案的 Visual Studio 規則的執行個體中，第一次規則的執行個體中安裝擴充功能。 然後，將偵錯工具附加至第二個 Visual Studio 處理序。 完成之後，您可以移除擴充功能，以便在開發電腦上不再載入。  
  
#### <a name="to-install-the-extension"></a>安裝擴充功能  
  
1.  關閉所有 Visual Studio 執行個體。  
  
2.  在組建輸出資料夾中的擴充功能專案中，開啟.vsix 檔案透過按兩下，或是開啟其捷徑功能表，然後選擇**開啟**:  
  
3.  在**Visual Studio 擴充功能安裝程式**對話方塊方塊中，選取您想要安裝擴充功能，再選擇的 Visual Studio 版本**安裝** 按鈕。  
  
     Visual Studio 會延伸檔案安裝至 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*作者姓名*\\*副檔名*\\*版本*。 這個路徑中的最後三個資料夾都從建構`Author`， `Name`，和`Version`extension.vsixmanifest 檔案延伸模組中的項目。  
  
4.  Visual Studio 安裝擴充功能之後，請選擇**關閉** 按鈕。  
  
#### <a name="to-debug-the-extension"></a>若要偵錯擴充功能  
  
1.  以系統管理員權限啟動 Visual Studio，然後開啟 擴充功能專案中。 下列步驟，請參閱 Visual Studio，做為這個執行個體*第一次執行個體*。  
  
2.  系統管理員權限啟動 Visual Studio 的另一個執行個體。 下列步驟，請參閱 Visual Studio，做為這個執行個體*第二個執行個體*。  
  
3.  切換至 Visual Studio 的第一個執行個體。  
  
4.  在功能表列上選擇 **偵錯**，**附加至處理序**。  
  
5.  在**可用的處理序**清單中，選擇 devenv.exe。 此項目是指 Visual Studio; 第二個執行個體這是您要偵錯您的專案擴充功能中的執行個體。  
  
6.  選擇**附加** 按鈕。  
  
     Visual Studio 偵錯模式中執行擴充功能專案中。  
  
7.  切換至 Visual Studio 的第二個執行個體。  
  
8.  建立新的 SharePoint 專案，以載入您的擴充功能。 例如，如果您正在偵錯擴充功能的清單定義專案項目，建立**清單定義**專案。  
  
9. 執行任何的步驟需要測試延伸模組程式碼。  
  
10. 當您完成偵錯擴充功能時，請關閉 Visual Studio 的第二個執行個體。  
  
#### <a name="to-remove-the-extension"></a>若要移除該擴充功能  
  
1.  在 Visual Studio 中，功能表列上選擇 **工具**，**擴充功能和更新**。  
  
     [擴充功能和更新] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，選擇延伸模組的名稱，然後選擇 [**解除安裝**] 按鈕。  
  
3.  在出現的對話方塊中，選擇 **是**按鈕，以確認您想要解除安裝擴充功能。  
  
4.  選擇**立即重新啟動**按鈕，以完成解除安裝。  
  
## <a name="debugging-sharepoint-commands"></a>偵錯 SharePoint 命令  
 如果您想要偵錯 SharePoint 命令的 SharePoint 工具擴充功能的一部分，您必須將偵錯工具附加至 vssphost4.exe 處理序。 這是執行 SharePoint 命令 64 位元主控件程序。 如需有關 SharePoint 命令和 vssphost4.exe 的詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>若要將偵錯工具附加至 vssphost4.exe 程序  
  
1.  開始偵錯您的 Visual Studio 實驗執行個體或規則的執行個體的 Visual Studio 中的延伸模組，遵循上述指示。  
  
2.  在 Visual Studio 中您正在偵錯工具，在功能表列的執行個體，選擇**偵錯**，**附加至處理序**。  
  
3.  在**可用的處理序**清單中，選擇 vssphost.exe。  
  
    > [!NOTE]  
    >  如果 vssphost.exe 沒有出現在清單中，您必須在您執行擴充功能的 Visual Studio 執行個體中啟動 vssphost4.exe 程序。 一般而言，您藉由執行使 Visual Studio 以連接至 SharePoint 網站，在開發電腦上的動作。 例如，Visual Studio 會啟動 vssphost4.exe 底下展開的站台連線節點 （節點會顯示網站 URL） 時**SharePoint 連接**中的節點**伺服器總管**視窗中，或當您將特定 SharePoint 專案項目，例如**清單執行個體**或**事件接收器**加入 SharePoint 專案項目。  
  
4.  選擇**附加** 按鈕。  
  
5.  在 Visual Studio 正在偵錯的執行個體，執行的步驟，才能執行您的命令。  
  
## <a name="modifying-registry-values-to-help-debug-sharepoint-tools-extensions"></a>修改登錄值，以協助偵錯 SharePoint 工具擴充功能  
 當您偵錯的 Visual Studio 中的 SharePoint 工具擴充功能時，您可以修改登錄，以協助您疑難排解擴充功能中的值。 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools 機碼下的值存在。 依預設不存在這些值。  
  
 若要疑難排解 SharePoint 工具的任何擴充功能，您可以建立及設定 EnableDiagnostics 值。 下表描述此值。  
  
|值|描述|  
|-----------|-----------------|  
|EnableDiagnostics|指定是否顯示診斷訊息中的 REG_DWORD**輸出**視窗。<br /><br /> 顯示診斷訊息，請將此值設定為 1。 若要停止顯示訊息，將此值設定為 0，或刪除此值。<br /><br /> 若要寫入訊息至**輸出**視窗從 SharePoint 工具擴充功能，請使用 SharePoint 專案服務。 如需詳細資訊，請參閱[使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。|  
  
 如果您的擴充功能包含 SharePoint 命令，您可以建立並設定其他的值，以協助疑難排解命令。 下表描述這些值。  
  
|值|描述|  
|-----------|-----------------|  
|AttachDebuggerToHostProcess|指定是否要顯示的對話方塊，可讓您將偵錯工具附加至 vssphost4.exe，只要它啟動的 REG_DWORD。 如果由 vssphost.exe 執行您要偵錯命令啟動之後，立即這非常有用，但沒有足夠的時間來執行命令之前，以手動方式附加偵錯工具。 若要顯示的對話方塊中，會呼叫 vssphost4.exe<xref:System.Diagnostics.Debugger.Break%2A>方法啟動時。<br /><br /> 啟用此行為，請將此值設定為 1。 若要關閉此行為，將此值設定為 0，或刪除此值。<br /><br /> 如果您設定此值為 1 時，您可能也要增加 HostProcessStartupTimeout 值，讓您有足夠的時間來附加偵錯工具，Visual Studio 要求 vssphost4.exe 發出信號，指出成功啟動之前。|  
|ChannelOperationTimeout|指定的時間，以秒為單位，Visual Studio 執行 SharePoint 命令的 REG_DWORD。 如果命令不會執行的時間，<xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>就會擲回。<br /><br /> 預設為 120 秒。|  
|HostProcessStartupTimeout|指定的時間，以秒為單位，Visual Studio vssphost4.exe 發出信號，如它的 REG_DWORD 已順利啟動。 如果 vssphost4.exe 不表示成功的開始時間，<xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>就會擲回。<br /><br /> 預設值為 60 秒。|  
|MaxReceivedMessageSize|指定允許的大小上限，以位元組為單位，Visual Studio 和 vssphost4.exe 之間傳遞的 WCF 訊息的 REG_DWORD。<br /><br /> 預設值為 1048576 個位元組 (1 MB)。|  
|MaxStringContentLength|REG_DWORD 指定允許的大小上限，單位為位元組的 Visual Studio 和 vssphost4.exe 之間傳遞的字串。<br /><br /> 預設值為 1048576 個位元組 (1 MB)。|  
  
## <a name="see-also"></a>另請參閱  
 [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [部署 Visual Studio 中 SharePoint 工具的延伸模組](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  