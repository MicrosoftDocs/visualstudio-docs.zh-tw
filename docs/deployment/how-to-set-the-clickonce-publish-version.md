---
title: 如何： 設定 ClickOnce 發行版本 |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea53e5e50aebc7c8ad201f6dae1003350f9fa4e2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633443"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>How to: Set the ClickOnce publish version (如何：設定 ClickOnce 發行版本)
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version`屬性會決定是否要發行的應用程式將會被視為更新。 每個階段的版本會遞增，將更新的形式發行應用程式。

 `Publish Version`上設定屬性**發佈**頁面**專案設計工具**。

> [!NOTE]
>  沒有專案 選項，將會自動遞增`Publish Version`屬性每次發行應用程式時，預設會啟用此選項。 如需詳細資訊，請參閱 <<c0> [ 如何： 自動累加 ClickOnce 發行版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)。

### <a name="to-change-the-publish-version"></a>若要變更的發行版本

1.  選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。

2.  按一下 [發佈] 索引標籤。

3.  在 **發行版本**欄位中，遞增**主要**，**次要**，**建置**，或**修訂**版本數字。

    > [!NOTE]
    >  您應該永遠不會遞減版本號碼;因此，這麼做可能會造成無法預期的更新行為。

## <a name="see-also"></a>另請參閱
- [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)
- [How to: Automatically increment the ClickOnce publish version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md) (如何：自動累加 ClickOnce 的發行版本)
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)