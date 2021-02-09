---
title: 變更 ClickOnce 應用程式的發行語言
description: 瞭解如何在 ClickOnce 中指定當地語系化應用程式的語言/文化特性，而不是預設為開發電腦的語言/文化特性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0d9c3d49dde0bdef41e89ee71139fb1ab621297
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851461"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>如何：變更 ClickOnce 應用程式的發佈語言

發佈 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，在安裝期間顯示的使用者介面預設為開發電腦的語言和文化特性。 如果您要發行當地語系化的應用程式，則必須指定語言和文化特性以符合當地語系化的版本。 這取決於 `Publish language` 您專案的屬性。

`Publish language`可以在 [**發行選項**] 對話方塊中設定屬性，可從 [**專案設計** 工具] 的 [**發行**] 頁面存取。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具] 功能表上選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="to-change-the-publish-language"></a>變更發行語言

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [Publish (發行)]  索引標籤。

3. 按一下 [ **選項** ] 按鈕，開啟 [ **發行選項** ] 對話方塊。

4. 按一下 [ **描述**]。

5. 在 [ **發行選項** ] 對話方塊中，從 [ **發行語言** ] 下拉式清單中選取語言和文化特性，然後按一下 **[確定]**。

## <a name="see-also"></a>另請參閱

- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)