---
title: 自動遞增 ClickOnce 發行版本
description: 瞭解如何使用 Visual Studio 來停用 ClickOnce 應用程式的修訂編號自動遞增。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84b0a8932bb9d8fd4738c2cd4924b61bb6faeb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947771"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>如何：自動累加 ClickOnce 的發佈版本

發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，變更 `Publish Version` 屬性會導致應用程式發佈為更新。 依預設，Visual Studio 會在 `Revision` `Publish Version` 每次發行應用程式時自動遞增的數目。

您可以在 [**專案設計** 工具] 的 [**發行**] 頁面上停用此行為。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具] 功能表上選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>若要停用自動遞增發行版本

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [Publish (發行)]  索引標籤。

3. 在 [ **發行版本** ] 區段中，清除 [ **自動遞增修訂與每個版本** ] 核取方塊。

## <a name="see-also"></a>另請參閱

- [How to: Set the ClickOnce publish version (如何：設定 ClickOnce 發行版本)](../deployment/how-to-set-the-clickonce-publish-version.md)
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)