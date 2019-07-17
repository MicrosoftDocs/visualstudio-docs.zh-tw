---
title: 部署 Windows 市集應用程式
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73b4350a2e7f277a11f4d6650d8089df0f87fe4d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177443"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>從 Visual Studio 部署 Windows 市集應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

僅適用於 Windows] (../Image/windows_only_content.png"windows_only_content")

 Visual Studio 部署功能會在目標裝置上建置和註冊使用 Visual Studio 建立的 Windows 市集應用程式。 應用程式的確切註冊方式取決於目標裝置是本機還是遠端：

- 目標是本機 Visual Studio 電腦時，Visual Studio 會從其組建資料夾中註冊應用程式。

- 目標是遠端裝置時，Visual Studio 會將必要檔案複製至遠端電腦，並在該裝置上註冊應用程式。

  當您使用偵錯您的應用程式，從 Visual Studio 部署便會自動**開始偵錯**選項 (鍵盤：F5) 或**啟動但不偵錯**選項 (鍵盤：CTRL + F5）。 您也可以手動部署應用程式。 手動部署適用於下列情況：

- 本機或遠端電腦上進行臨機操作測試。

- 部署將啟動另一個您要偵錯之應用程式的應用程式。

- 部署應用程式，以另一個應用程式或另一種方法啟動該應用程式時，對其進行偵錯。

## <a name="BKMK_In_this_topic"></a> 本主題內容
 在本主題中，您可以了解：

 [如何部署 Windows 市集應用程式](#BKMK_How_to_deploy_a_Windows_Store_app)

 [如何指定遠端裝置](#BKMK_How_to_specify_a_remote_device)

 [部署選項](#BKMK_Deployment_options)

## <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> 如何部署 Windows 市集應用程式
 手動部署應用程式是一個簡單的流程：

1. 如果您部署至遠端裝置，請在應用程式啟始專案的屬性專案頁面中指定裝置的名稱或 IP 位址。 (本主題會進一步列出這項作業的步驟)。

2. 在偵錯工具 Visual Studio 工具列上，從 [開始偵錯]  按鈕旁邊的下拉式清單中選擇部署目標。

     ![在本機電腦上執行](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3. 在 [建置]  功能表上，選擇 [部署] 

## <a name="BKMK_How_to_specify_a_remote_device"></a> 如何指定遠端裝置
 **必要條件**

 將應用程式部署至遠端裝置：

- 遠端裝置上必須安裝開發人員授權。

- Visual Studio 遠端工具必須安裝在遠端裝置上，而且遠端偵錯監視必須正在執行。

     部署使用遠端偵錯工具網路通道，將應用程式檔案傳送至遠端裝置。

#### <a name="to-specify-a-remote-device"></a>指定遠端裝置

1. 在啟始專案的 [偵錯] 屬性頁上，指定遠端部署目標的名稱或 IP 位址。

2. 若要開啟 [偵錯] 屬性頁，請在 [方案總管] 中選擇專案，然後從捷徑功能表中選擇 [屬性]  。

3. 然後選擇屬性頁視窗上的 [偵錯]  節點。

4. 您可以輸入遠端裝置的名稱或 IP 位址，也可以從 [選取遠端偵錯工具連接]  對話方塊中選擇裝置。

    ![選取遠端偵錯工具連接 對話方塊](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    [選取遠端偵錯工具連接]  對話方塊會顯示本機子網路上的裝置，以及透過乙太網路纜線直接連接至 Visual Studio 電腦的任何裝置。

   **在 JavaScript 或 Visual C++ 專案頁面中指定遠端裝置**

   ![C&#43; &#43;的專案進行遠端偵錯的屬性](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. 從 [ **要啟動的偵錯工具** ] 清單選擇 [ **遠端偵錯工具** ]。

6. 在 [電腦名稱]  方塊中，輸入遠端裝置的網路名稱。 或者，您可以選擇方塊中的向下箭頭，以從 [選取遠端偵錯工具連接] 對話方塊中選取裝置。

   **在 Visual C# 和 Visual Basic 專案頁面中指定遠端裝置**

   ![受管理的遠端偵錯專案屬性](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. 從 [ **目標裝置** ] 清單選擇 [ **遠端電腦** ]。

8. 在 [ **遠端電腦** ] 方塊中輸入遠端裝置的網路名稱，或按一下 [ **尋找** ]，從 [ **選取遠端偵錯工具連接** ] 對話方塊選擇裝置。

## <a name="BKMK_Deployment_options"></a> 部署選項
 您可以在啟始專案的 [偵錯] 屬性頁上設定下列部署選項。

 **允許網路 Loopback**基於安全性理由，[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]以標準方式安裝應用程式不允許進行到其安裝所在裝置的網路呼叫。 根據預設，Visual Studio 部署會針對部署應用程式建立此規則的豁免。 此豁免可讓您測試在單一機器上的通訊程序。 在將您的應用程式提交至 [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]之前，您應該在沒有豁免的情況下測試您的應用程式。

 移除應用程式中的網路回送豁免：

- 在 [C# 和 VB 偵錯] 屬性頁上，清除 [允許網路回送]  核取方塊。

- 在 [JavaScript 偵錯] 屬性頁上，將 [允許網路回送]  值設定為 [否]  。

  **不啟動，但啟動時，將我的程式碼進行偵錯 (C#和 VB) / 啟動應用程式 (JavaScript 和C++)** 來設定為自動啟動應用程式啟動時的偵錯工作階段的部署：

- 在 [C# 和 VB 偵錯] 屬性頁上，核取 [不啟動，但在我的程式碼啟動時進行偵錯]  核取方塊。

- 在 [JavaScript 偵錯] 屬性頁上，將 [啟動應用程式]  值設定為 [是]  。

## <a name="see-also"></a>另請參閱
 [從 Visual Studio 執行應用程式](../debugger/run-store-apps-from-visual-studio.md)
