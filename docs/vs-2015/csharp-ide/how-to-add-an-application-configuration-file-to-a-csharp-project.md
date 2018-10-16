---
title: 如何： 將應用程式組態檔加入 C# 專案 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 43245704a2393b298f0f1d948d8a8829a4ef9bc4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204785"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>如何：將應用程式組態檔加入至 C# 專案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以將應用程式組態檔 (app.config 檔案) 加入 C# 專案，以自訂通用語言執行平台尋找及載入組件檔的方式。 如需有關應用程式組態檔的詳細資訊，請參閱[執行階段如何找出組件](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)。  
  
> [!NOTE]
>  不支援 Windows 市集<xref:System.Configuration>。 如此一來，市集應用程式不包含 app.config 範本。  
  
 當您建置專案時，開發環境會自動複製您的 app.config 檔案會變更以符合您的可執行檔複製的檔案名稱，然後移動到 bin 目錄。  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>若要將應用程式組態檔新增至您的 C# 專案  
  
1.  在功能表列上選擇 **專案**，**加入新項目**。  
  
     [新增項目] 對話方塊隨即出現。  
  
2.  依序展開**已安裝**，展開**Visual C# 項目**，然後選擇**應用程式組態檔**範本。  
  
3.  在 [名稱] 文字方塊中，輸入名稱，然後選擇 [新增] 按鈕。  
  
     名為 app.config 檔案會加入至您的專案中。  
  
## <a name="see-also"></a>另請參閱  
 [管理應用程式設定 (.NET)](../ide/managing-application-settings-dotnet.md)   
 [組態檔結構描述](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [設定應用程式](http://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [如何： 設定.NET Framework 版本為目標的應用程式](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [使用 C# 的 Visual Studio 開發環境](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)