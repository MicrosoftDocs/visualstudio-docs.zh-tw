---
title: 使用 ClickOnce 應用程式安裝必要條件
description: 瞭解如何選取必要元件，以便在安裝時與 ClickOnce 應用程式一起封裝。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09337ee164c8b740e9aa8a044c4a9df385f01016
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900559"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>How to: Install prerequisites with a ClickOnce application (如何：使用 ClickOnce 應用程式安裝必要元件)
所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式都需要在電腦上安裝正確的 .NET Framework 版本，才能執行這些應用程式; 許多應用程式也有其他必要條件。 發佈 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，您可以選擇要與應用程式一起封裝的一組必要條件元件。 在安裝時，將會針對每個必要條件執行檢查，以判斷它是否已存在;如果不是，則會在安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式之前安裝。

 您也可以指定元件的下載位置，而不是封裝和發佈必要條件。 例如，您可能會在安裝期間使用集中式檔案共用或包含所有必要條件安裝程式的 Web 位置，而不是包含必要條件，而是從該位置下載並安裝元件。

> [!IMPORTANT]
> 您應該先將先決條件安裝程式套件新增至您的開發電腦，然後再發佈第一個 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。 如需詳細資訊，請參閱 [如何：將必要條件納入 ClickOnce 應用程式](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md)。

 必要條件是在 [**必要條件**] 對話方塊中管理的，可從 [**專案設計** 工具] 的 [**發行**] 窗格存取。

> [!NOTE]
> 除了預先決定的必要條件清單之外，您還可以將自己的元件新增至清單。 如需詳細資訊，請參閱建立啟動載入器 [套件](../deployment/creating-bootstrapper-packages.md)。

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>若要指定要使用 ClickOnce 應用程式安裝的必要條件

1. 在 **方案總管** 中選取專案時，在 [ **專案** ] 功能表上按一下 [ **屬性**]。

2. 選取 [ **發行** ] 窗格。

3. 按一下 [ **必要條件** ] 按鈕以開啟 [ **必要條件** ] 對話方塊。

4. 在 [ **必要條件** ] 對話方塊中，確定已選取 [ **建立安裝程式以安裝必要條件元件** ] 核取方塊。

5. 在 [ **必要條件** ] 清單中，檢查您要安裝的元件，然後按一下 **[確定]**。

     選取的元件將會隨您的應用程式一起封裝和發佈。

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>針對必要條件指定不同的下載位置

1. 在 **方案總管** 中選取專案時，在 [ **專案** ] 功能表上按一下 [ **屬性**]。

2. 選取 [ **發行** ] 窗格。

3. 按一下 [ **必要條件** ] 按鈕以開啟 [ **必要條件** ] 對話方塊。

4. 在 [ **必要條件** ] 對話方塊中，確定已選取 [ **建立安裝程式以安裝必要條件元件** ] 核取方塊。

5. 在 [ **指定必要條件的安裝位置** ] 區段中，選取 **[從下列位置下載必要條件**]。

6. 從下拉式清單中選取位置，或輸入 URL、檔案路徑或 FTP 位置，然後按一下 **[確定]。**

    > [!NOTE]
    > 您必須確認指定的元件的安裝程式存在於指定的位置。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)