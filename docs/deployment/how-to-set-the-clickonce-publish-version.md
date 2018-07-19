---
title: 如何： 設定 ClickOnce 發行版本 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c991975a369387fea248816f4465670f1062a927
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080222"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>如何： 設定 ClickOnce 發行版本
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version`屬性會決定是否要發行的應用程式將會被視為更新。 每個階段的版本會遞增，將更新的形式發行應用程式。  
  
 `Publish Version`上設定屬性**發佈**頁面**專案設計工具**。  
  
> [!NOTE]
>  沒有專案 選項，將會自動遞增`Publish Version`屬性每次發行應用程式時，預設會啟用此選項。 如需詳細資訊，請參閱 <<c0> [ 如何： 自動累加 ClickOnce 發行版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)。  
  
### <a name="to-change-the-publish-version"></a>若要變更的發行版本  
  
1.  選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。  
  
2.  按一下 [**發佈**] 索引標籤。  
  
3.  在 **發行版本**欄位中，遞增**主要**，**次要**，**建置**，或**修訂**版本數字。  
  
    > [!NOTE]
    >  您應該永遠不會遞減版本號碼;因此，這麼做可能會造成無法預期的更新行為。  
  
## <a name="see-also"></a>另請參閱  
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [如何： 自動累加 ClickOnce 的發行版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)