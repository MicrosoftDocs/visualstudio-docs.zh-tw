---
title: 如何： 停用 ClickOnce 應用程式的 URL 啟動 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ad43abbafe1d5f70bb2de748154a0066aa3d8927
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488377"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>如何：停用 ClickOnce 應用程式的 URL 啟動過程
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 停用 URL 啟用的 ClickOnce 應用程式](https://docs.microsoft.com/visualstudio/deployment/how-to-disable-url-activation-of-clickonce-applications)。  
  
一般而言，從 Web 伺服器安裝 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式後，其將立即自動啟動。 基於安全性理由，您可能決定要停用此行為，並告知使用者啟動應用程式**啟動**功能表改。 下列程序描述如何停用 URL 啟用。  
  
 這項技術僅適用於安裝在使用者電腦上的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，其來自 Web 伺服器。 此技術不得用於僅限線上使用的應用程式，其只能使用 URL 啟動。 如需有關線上專用和已安裝的應用程式之間的差異的詳細資訊，請參閱[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 此程序使用 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] 工具 MageUI.exe。 如需有關這項工具的詳細資訊，請參閱 < [MageUI.exe (Manifest Generation and Editing Tool，Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)。 您也可以使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 執行這項程序。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-disable-url-activation-for-your-application"></a>若要停用應用程式的 URL 啟用  
  
1.  開啟 MageUI.exe 中的部署資訊清單。 如果您尚未建立一個，請依照下列中的步驟[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
2.  選取 [**部署選項**] 索引標籤。  
  
3.  清除**自動執行安裝後的應用程式**核取方塊。  
  
4.  儲存並簽署該資訊清單。  
  
## <a name="see-also"></a>另請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)



