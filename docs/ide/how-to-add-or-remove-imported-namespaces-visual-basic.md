---
title: 新增或移除匯入的命名空間 (Visual Basic)
description: 瞭解如何新增或移除匯入的命名空間，以及新增或移除使用者匯入。
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: how-to
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18e3010e9798f3c056afd5ffc7964ace3f734f53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970838"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>如何：新增或移除匯入的命名空間 (Visual Basic)

匯入命名空間可讓您在程式碼中使用該命名空間中的項目，而不需要完全符合項目。 例如，如果您想要存取 `System.Messaging.MessageQueue` 類別中的 `Create` 方法，則可以匯入 `System.Messaging` 命名空間，而且只將程式碼中您需要的項目參照為 `MessageQueue.Create`。

匯入的命名空間是在 [專案設計工具] 的 [參考] 頁面上進行管理。 您在此對話方塊中所指定的匯入會直接傳遞至編譯器 (*/imports*)，並套用至您專案中的所有檔案。 使用 `Imports` 陳述式，以在單一原始程式碼檔中使用命名空間。

### <a name="to-add-an-imported-namespace"></a>新增匯入的命名空間

1. 在方案總管中，按兩下專案的 [我的專案] 節點。

2. 在 [專案設計工具] 中，按一下 [參考] 索引標籤。

3. 在 [匯入的命名空間] 清單中，選取您要新增之命名空間的核取方塊。

    > [!NOTE]
    > 若要匯入，命名空間必須位在參考的元件中。 如果命名空間未出現在清單中，則您必須將參考新增至包含它的元件中。 如需詳細資訊，請參閱 [管理專案中的參考](managing-references-in-a-project.md)。

### <a name="to-remove-an-imported-namespace"></a>移除匯入的命名空間

1. 在方案總管中，按兩下專案的 [我的專案] 節點。

2. 在 [專案設計工具] 中，按一下 [參考] 索引標籤。

3. 在 [匯入的命名空間] 清單中，清除您要移除之命名空間的核取方塊。

## <a name="user-imports"></a>使用者匯入
使用者匯入可讓您匯入命名空間內的特定類別，而不是整個命名空間。 例如，您的應用程式可能有 <xref:System.Diagnostics> 命名空間的匯入，但該命名空間內您感興趣的唯一類別是 `Debug` 類別。 您可以將 <xref:System.Diagnostics.Debug> 定義為使用者匯入，然後移除 <xref:System.Diagnostics> 的匯入。

如果您稍後變更想法，並決定這實際上是您需要的 `EventLog` 類別，則可以輸入 <xref:System.Diagnostics.EventLog> 作為使用者匯入，並使用更新功能來覆寫 <xref:System.Diagnostics.Debug>。

### <a name="to-add-a-user-import"></a>新增使用者匯入

1. 在方案總管中，按兩下專案的 [我的專案] 節點。

2. 在 [專案設計工具] 中，按一下 [參考] 索引標籤。

3. 在 [匯入的命名空間] 清單下方的文字方塊中，輸入您要匯入之命名空間的完整名稱 (包括根命名空間)。

4. 按一下 [新增使用者匯入] 按鈕，將命名空間新增至 [匯入的命名空間] 清單。

    > [!NOTE]
    > 如果命名空間符合清單中的現有命名空間，則會停用 [新增使用者匯入] 按鈕；您不能將匯入新增兩次。

### <a name="to-update-a-user-import"></a>更新使用者匯入

1. 在方案總管中，按兩下專案的 [我的專案] 節點。

2. 在 [專案設計工具] 中，按一下 [參考] 索引標籤。

3. 在 [匯入的命名空間] 清單中，選取您要變更的命名空間。

4. 在 [匯入的命名空間] 清單下方的文字方塊中，輸入新命名空間的名稱。

5. 按一下 [更新使用者匯入] 按鈕，更新 [匯入的命名空間] 清單中的命名空間。

## <a name="see-also"></a>另請參閱

- [管理專案中的參考](../ide/managing-references-in-a-project.md)
