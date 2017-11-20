---
title: "ClickOnce 執行應用程式更新的方式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 32e0b56ab5d4507c971948b98c8f7660650e70cc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce 執行應用程式更新的方式
ClickOnce 會使用應用程式的部署資訊清單中指定的檔案版本資訊決定是否要更新應用程式的檔案。 更新開始之後，ClickOnce 會使用稱為技術*修補檔案*避免重複下載的應用程式檔案。  
  
## <a name="file-patching"></a>修補程式的檔案  
 在更新應用程式時，ClickOnce 不會下載新版本的應用程式檔案的所有除非檔案已變更。 相反地，它會比較目前的應用程式資訊清單為新的版本中的簽章的應用程式資訊清單中指定的檔案的雜湊簽章。 如果檔案的簽章不同，ClickOnce 會下載新的版本。 如果簽章相符，檔案已不變更從一個版本，為下一步。 在此情況下，ClickOnce 複製現有的檔案，並使用新版本的應用程式中。 這種方法可避免 ClickOnce 下載和整個應用程式一次，即使只需要一個或兩個檔案已有所變更。  
  
 修補檔案需視需要使用也適用於下載的組件<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A>和<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A>方法。  
  
 如果您使用 Visual Studio 來編譯您的應用程式，將會產生新的雜湊簽章的所有檔案，每當您重建整個專案。 在此情況下，所有組件會下載至用戶端，雖然只有少數的組件可能已變更。  
  
 修補檔案不適用於標示為資料和資料目錄中儲存的檔案。 這些檔案的雜湊簽章不論一律都會下載。 如需有關資料目錄的詳細資訊，請參閱[存取本機和 ClickOnce 應用程式中的遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。  
  
## <a name="see-also"></a>另請參閱  
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)