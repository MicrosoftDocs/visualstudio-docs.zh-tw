---
title: 偵錯已發佈的 Azure 雲端服務的使用 Visual Studio 和 IntelliTrace |Microsoft Docs
description: 了解如何使用雲端服務 Visual Studio 和 IntelliTrace 進行偵錯
author: mikejo5000
manager: douge
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 865642bb7c8e41f81ff4b44ce628082e19b63a56
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002010"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>使用 Visual Studio 與and IntelliTrace 針對已發佈的 Azure 雲端服務進行偵錯
如果有 IntelliTrace，您可以在 Azure 中執行時記錄的角色執行個體的廣泛偵錯資訊。 如果您需要找出問題的原因，您可以使用 IntelliTrace 記錄檔，如同它已在 Azure 中執行，逐步執行程式碼從 Visual Studio。 實際上，IntelliTrace 會記錄主要執行程式碼和環境資料時，Azure 應用程式當做雲端服務在 Azure 中執行，而且可讓您重新執行記錄的資料，從 Visual Studio。 

您可以使用 IntelliTrace，如果您已安裝的 Visual Studio Enterprise 與您 Azure 應用程式的目標.NET Framework 4 或更新版本。 IntelliTrace 會收集 Azure 角色的資訊。 這些角色的虛擬機器一律會執行 64 位元作業系統。

或者，您可以使用[遠端偵錯](http://go.microsoft.com/fwlink/p/?LinkId=623041)以直接附加到執行於 Azure 雲端服務。

> [!IMPORTANT]
> IntelliTrace 適用於偵錯，並不應該用於生產環境部署。
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>針對 IntelliTrace 設定 Azure 應用程式
若要啟用 Azure 應用程式的 IntelliTrace，您必須建立並發行應用程式從 Visual Studio Azure 專案。 發行至 Azure 之前，您必須將 IntelliTrace 設定 Azure 應用程式中。 如果您未設定 IntelliTrace 發行您的應用程式，您需要重新發佈專案。 如需詳細資訊，請參閱 <<c0> [ 發佈 Azure 雲端服務專案使用 Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623012)。

1. 當您準備好要部署 Azure 應用程式時，確認專案建置目標會設定為**偵錯**。

1. 在 **方案總管**，以滑鼠右鍵按一下專案，並從操作功能表中，選取**發佈**。
   
1. 在 [**發佈 Azure 應用程式**對話方塊中，選取 Azure 訂用帳戶，然後選取**下一步]**。

1. 在 [**設定**頁面上，選取**進階設定**] 索引標籤。

1. 開啟**啟用 IntelliTrace**選項，即可發行至雲端時收集您的應用程式的 IntelliTrace 記錄檔。
   
1. 若要自訂基本的 IntelliTrace 組態，請選取**設定**旁**啟用 IntelliTrace**。

    ![IntelliTrace 設定連結](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. 在 [ **IntelliTrace 設定**] 對話方塊中，您可以指定要記錄、 是否要收集呼叫資訊、 模組和處理序收集記錄檔，以及記錄配置多少空間的事件。 如需有關 IntelliTrace 的詳細資訊，請參閱 <<c0> [ 使用 IntelliTrace 偵錯](http://go.microsoft.com/fwlink/?LinkId=214468)。
   
    ![IntelliTrace 設定](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

IntelliTrace 記錄檔是循環記錄檔 （預設大小為 250 MB） 的 IntelliTrace 設定中指定的大小上限。 IntelliTrace 記錄檔會收集虛擬機器的檔案系統中的檔案。 當您要求記錄檔時，快照集是在該點時間取得，並下載到本機電腦。

Azure 雲端服務發佈至 Azure 之後，您可以判斷是否已從 [Azure] 節點中啟用 IntelliTrace**伺服器總管**，如下圖所示：

![伺服器總管-已啟用 IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>下載角色執行個體的 IntelliTrace 記錄檔
使用 Visual Studio，您可以依照下列步驟下載角色執行個體的 IntelliTrace 記錄檔：

1. 在 [**伺服器總管**，展開**雲端服務**] 節點，並找出角色執行個體為您想要下載的記錄檔。 

1. 以滑鼠右鍵按一下角色執行個體，並從操作功能表中，選取**檢視 IntelliTrace 記錄檔**。 

    ![檢視 IntelliTrace 記錄檔 功能表選項](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. IntelliTrace 記錄檔會下載到本機電腦上的檔案的目錄中。 每當您要求 IntelliTrace 記錄檔，建立新的快照。 下載記錄檔時，Visual Studio 會顯示在作業進度**Azure 活動記錄檔**視窗。 下圖所示，您可以展開明細項目，以查看詳細資料作業。

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

您可以繼續在 Visual Studio IntelliTrace 記錄檔會下載工作。 當記錄檔完成下載時，它會在 Visual Studio 中開啟。

> [!NOTE]
> IntelliTrace 記錄檔可能包含架構隨後產生並處理的例外狀況。 內部架構程式碼會產生在正常啟動角色，因此您可以放心地忽略這些例外狀況。
> 
> 

## <a name="next-steps"></a>後續步驟
- [進行偵錯 Azure 雲端服務選項](vs-azure-tools-debugging-cloud-services-overview.md)
- [發佈使用 Visual Studio，在 Azure 雲端服務](vs-azure-tools-publishing-a-cloud-service.md)