---
title: 設定 ClickOnce 發行版本 |Microsoft Docs
description: 瞭解如何設定 ClickOnce 發佈版本屬性，以決定應用程式是否為更新。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71d74d8b16e058b150187a231a1f3a7323c0c612
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885023"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>How to: Set the ClickOnce publish version (如何：設定 ClickOnce 發行版本)
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` 屬性會決定您要發佈的應用程式是否會被視為更新。 每次版本都會遞增，應用程式將會發佈為更新。

 您 `Publish Version` 可以在 [**專案設計** 工具] 的 [**發行**] 頁面上設定屬性。

> [!NOTE]
> 專案選項會在 `Publish Version` 每次發行應用程式時自動遞增屬性; 此選項預設為啟用。 如需詳細資訊，請參閱 [如何：自動遞增 ClickOnce 發行版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)。

### <a name="to-change-the-publish-version"></a>變更發行版本

1. 在 **方案總管** 中選取專案時，在 [ **專案** ] 功能表上按一下 [ **屬性**]。

2. 按一下 [Publish (發行)]  索引標籤。

3. 在 [ **發行版本** ] 欄位中，遞增 **主要**、 **次要**、 **組建** 或 **修訂** 版本號碼。

    > [!NOTE]
    > 您永遠不應該遞減版本號碼;這樣做可能會導致無法預期的更新行為。

## <a name="see-also"></a>另請參閱
- [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)
- [How to: Automatically increment the ClickOnce publish version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md) (如何：自動累加 ClickOnce 的發行版本)
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)