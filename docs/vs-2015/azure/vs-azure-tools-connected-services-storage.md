---
title: 在 Visual Studio 中使用已連接服務加入 Azure 儲存體 |Microsoft Docs
description: 使用 Visual Studio 加入已連接服務對話方塊中，將 Azure 儲存體新增至您的應用程式
author: ghogen
manager: douge
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 63b796d9c514602a40f15b5725c07b1b89787df1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001395"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>使用 Visual Studio 已連接服務加入 Azure 儲存體
使用 Visual Studio 中，您可以下列任何一個使用連接到 Azure 儲存體**加入已連接服務**對話方塊：

- C#雲端服務
- .NET 後端行動服務
- ASP.NET 網站或服務
- ASP.NET Core 服務
- Azure WebJob 服務 

已連接的服務功能會將所有必要的參考和連接程式碼新增至您的專案，並適當地修改組態檔。 

完成之後，**加入已連接服務**對話方塊會自動顯示文件，裡面的步驟才能開始使用 blob 儲存體、 佇列和資料表。

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>連接到 Azure 儲存體已連接服務對話方塊
1. 在 Visual Studio 中開啟您的專案

1. 在**方案總管**，以滑鼠右鍵按一下**已連接服務**節點，然後從操作功能表，然後選取**加入已連接服務**。
   
    ![將 Azure 新增連線服務](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. 在 **已連線的服務**頁面上，選取**搭配 Azure 儲存體的雲端儲存體**。
   
    ![新增 Azure 儲存體](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. 在  **Azure 儲存體**對話方塊中，選取現有的儲存體帳戶，然後選取**新增**。
   
    如果您需要建立儲存體帳戶，請移至下一個步驟。 否則，請跳至步驟 6。
    
    ![將現有的儲存體帳戶新增至專案](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. 若要建立儲存體帳戶： 
   
   1. 選取 **建立新的儲存體帳戶**對話方塊的底部。

   1. 填寫**建立儲存體帳戶** 對話方塊中，然後選取**建立**。
      
       ![新的 Azure 儲存體帳戶](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)
      
   1. 當**Azure 儲存體** 對話方塊隨即出現，新的儲存體帳戶會出現在清單中。 在清單中，選取新的儲存體帳戶，然後選取**新增**。

1. 已連線的服務之下的儲存體**服務參考**在專案的節點。
   
## <a name="how-your-project-is-modified"></a>您的專案修改方式
當您完成 [] 對話方塊中時，Visual Studio 會將參考加入和修改某些組態檔。 特定變更視專案類型而定： 

- ASP.NET 專案-[發生什麼情形 – ASP.NET 專案](http://go.microsoft.com/fwlink/p/?LinkId=513126)
- ASP.NET Core 專案-[發生什麼情形 – ASP.NET 5 專案](http://go.microsoft.com/fwlink/p/?LinkId=513124) 
- 雲端服務專案 （web 角色和背景工作角色）-[發生什麼情形 – 雲端服務專案](http://go.microsoft.com/fwlink/p/?LinkId=516965)
- WebJob 專案-[發生什麼情形 – WebJob 專案](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>後續步驟
- [MSDN 論壇︰ Azure 儲存體](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Microsoft Azure 儲存體團隊部落格](http://blogs.msdn.com/b/windowsazurestorage/)
- [Azure 儲存體文件](https://docs.microsoft.com/azure/storage/)
