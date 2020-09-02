---
title: 如何：使用設計工具停用 ClickOnce 應用程式的 URL 啟用 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27690ab275d0c7ef2a090fa8ef2e42887ae9daeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153804"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>如何：使用設計工具停用 ClickOnce 應用程式的 URL 啟動過程
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

一般而言， [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式會在從 Web 服務器安裝之後，立即自動啟動。 基於安全性理由，您可以決定停用此行為，並告知使用者改從 [ **開始** ] 功能表啟動應用程式。 下列程序描述如何停用 URL 啟用。  
  
 這項技術僅適用於安裝在使用者電腦上的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，其來自 Web 伺服器。 它無法用於僅供線上使用的應用程式，只能使用其 URL 來啟動。 如需僅限線上和已安裝應用程式之間差異的詳細資訊，請參閱 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 此程式使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 您也可以使用來完成這項工作 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] 。 如需詳細資訊，請參閱 [如何：停用 ClickOnce 應用程式的 URL 啟用](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-disable-url-activation-for-your-application"></a>若要停用應用程式的 URL 啟用  
  
1. 在 **方案總管**中的專案名稱上按一下滑鼠右鍵，然後按一下 [ **屬性**]。  
  
2. 在 [ **屬性** ] 頁面上，按一下 [ **發行** ] 索引標籤。  
  
3. 按一下 [選項]。  
  
4. 按一下 [ **資訊清單**]。  
  
5. 選取標示為 [ **封鎖應用程式**] 的核取方塊，以透過 URL 啟用。  
  
6. 部署應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
