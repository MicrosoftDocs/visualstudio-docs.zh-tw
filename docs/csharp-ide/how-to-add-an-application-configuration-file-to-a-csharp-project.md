---
title: "如何： 將應用程式組態檔加入至 C# 專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 707100d33e91d1b0920d008140dc2fb6f1e078fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>如何：將應用程式組態檔加入至 C# 專案
將應用程式組態檔 （app.config 檔案） 加入至 C# 專案，您可以自訂 common language runtime 如何找出並載入組件檔案。 如需應用程式組態檔的詳細資訊，請參閱[執行階段如何找出組件](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)。  
  
> [!NOTE]
>  UWP 應用程式不包含 app.config 範本。
  
 當您建置專案時，開發環境會自動複製到您的 app.config 檔案會變更以符合您的可執行檔複製的檔案名稱，接著移至 bin 目錄的 複製。  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>若要將應用程式組態檔加入至您的 C# 專案  
  
1.  在功能表列上選擇 **專案**，**加入新項目**。  
  
     [新增項目] 對話方塊隨即出現。  
  
2.  展開**已安裝**，依序展開**Visual C# 項目**，然後選擇 **應用程式組態檔**範本。  
  
3.  在**名稱** 文字方塊中，輸入名稱，然後選擇**新增** 按鈕。  
  
     名為 app.config 的檔案加入至您的專案。  
  
## <a name="see-also"></a>請參閱  
 [管理應用程式設定 (.NET)](../ide/managing-application-settings-dotnet.md)   
 [組態檔結構描述](/dotnet/framework/configure-apps/file-schema/index)   
 [設定應用程式](/dotnet/framework/configure-apps/index)   
 [如何： 設定.NET Framework 版本為目標的應用程式](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [使用 C# 的 Visual Studio 開發環境](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)