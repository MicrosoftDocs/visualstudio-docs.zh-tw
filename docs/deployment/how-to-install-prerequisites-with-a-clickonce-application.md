---
title: HOW TO：使用 ClickOnce 應用程式安裝必要條件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0535ec606722ec162804718e7ee14bdd4714f4b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077006"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>HOW TO：隨著 ClickOnce 應用程式安裝必要軟體
所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式需要它們才能執行，在電腦上安裝正確版本的.NET framework; 許多應用程式以及其他必要條件。 發佈時[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式中，您可以選擇一組與您的應用程式一起封裝的必要元件。 在安裝期間，會檢查以判斷它是否已經存在; 每個必要條件如果在安裝之前未將已安裝[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。

 而不是封裝和發行必要條件，您也可以指定元件的下載位置。 比方說，而不是包含每個應用程式，您將發行的必要條件，您可以使用集中式的檔案共用或包含的所有必要條件的安裝程式的 Web 位置，在安裝時，將下載的元件和安裝從該位置。

> [!IMPORTANT]
>  您應該將必要條件安裝程式封裝加入您的開發電腦，然後再發行您的第一個[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。 如需詳細資訊，請參閱[如何：隨著 ClickOnce 應用程式納入必要軟體](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md)。

 在進行管理的必要條件**必要條件** 對話方塊中，從可存取**發佈**窗格**專案設計工具**。

> [!NOTE]
>  除了預先決定的必要條件清單中，您可以將自己的元件加入清單。 如需詳細資訊，請參閱 <<c0> [ 建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)。

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>若要指定要使用 ClickOnce 應用程式安裝的必要條件

1. 選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。

2. 選取 **發佈**窗格。

3. 按一下 **必要條件** 按鈕以開啟**必要條件** 對話方塊。

4. 在 [ **必要條件** ] 對話方塊中，確定已選取 [ **建立安裝程式以安裝必要條件元件** ] 核取方塊。

5. 在 **必要條件**清單中，檢查您想要安裝，然後按一下 元件**確定**。

     將封裝和發行您的應用程式以及選取的元件。

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>若要指定不同的下載位置的必要條件

1. 選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。

2. 選取 **發佈**窗格。

3. 按一下 **必要條件** 按鈕以開啟**必要條件** 對話方塊。

4. 在 [ **必要條件** ] 對話方塊中，確定已選取 [ **建立安裝程式以安裝必要條件元件** ] 核取方塊。

5. 在 **指定必要條件的安裝位置**區段中，選取**從下列位置下載必要條件**。

6. 從下拉式清單中，選取位置或輸入 URL、 檔案路徑或 FTP 位置，然後按一下 **[確定]。**

    > [!NOTE]
    >  您必須確定在安裝程式指定的元件存在於指定的位置。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)