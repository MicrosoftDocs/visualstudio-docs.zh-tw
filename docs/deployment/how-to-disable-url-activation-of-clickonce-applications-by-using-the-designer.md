---
title: "如何： 使用設計工具停用 ClickOnce 應用程式的 URL 啟用 |Microsoft 文件"
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
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d4df4bab3b3dd7ed29dd3e5d3ca2ff7e56c1922d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>如何：使用設計工具停用 ClickOnce 應用程式的 URL 啟動過程
一般而言，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安裝從 Web 伺服器後立即應用程式會自動啟動。 基於安全性理由，您可能決定要停用此行為，並告知使用者啟動應用程式從**啟動**功能表改為。 下列程序描述如何停用 URL 啟用。  
  
 這項技術僅適用於安裝在使用者電腦上的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，其來自 Web 伺服器。 它不能用於僅線上應用程式，而且可以啟動只能藉由使用其 URL。 如需有關僅限線上且已安裝的應用程式之間差異的詳細資訊，請參閱[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 此程序使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 您也可以完成這項工作中使用[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]。 如需詳細資訊，請參閱[如何： 停用 URL 啟用 ClickOnce 應用程式的](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-disable-url-activation-for-your-application"></a>若要停用應用程式的 URL 啟用  
  
1.  以滑鼠右鍵按一下您的專案名稱中**方案總管 中**，然後按一下**屬性**。  
  
2.  在**屬性**頁面上，按一下**發行** 索引標籤。  
  
3.  按一下 [選項] 。  
  
4.  按一下**資訊清單**。  
  
5.  選取標示的核取方塊**妨礙應用程式，使其無法透過 URL 啟動**。  
  
6.  部署您的應用程式。  
  
## <a name="see-also"></a>請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)