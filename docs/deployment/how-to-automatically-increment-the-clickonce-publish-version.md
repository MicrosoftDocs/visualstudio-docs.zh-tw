---
title: 如何： 自動累加 ClickOnce 的發行版本 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7dd1723d9d92d9bc1b667cc3fddbc3ea297d8b8
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389120"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>如何：自動累加 ClickOnce 的發佈版本

發佈時[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式中，變更`Publish Version`屬性可讓應用程式以更新形式發行。 根據預設，Visual Studio 會自動遞增`Revision`數目`Publish Version`每次發行應用程式。

您可以在停用此行為**發佈**頁**專案設計工具**。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>若要停用 自動遞增發行版本

1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2.  按一下 [發佈] 索引標籤。

3.  在 **發行版本**區段中，清除**隨著每次發行自動遞增修訂**核取方塊。

## <a name="see-also"></a>另請參閱

- [如何：設定 ClickOnce 發佈版本](../deployment/how-to-set-the-clickonce-publish-version.md)
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)