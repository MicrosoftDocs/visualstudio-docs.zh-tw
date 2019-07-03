---
title: 針對未匯入的型別完成 IntelliSense
description: 如何針對您尚未匯入的型別搭配 `using` 指示詞使用 IntelliSense 完成。
ms.date: 06/20/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f313cfa8520e4c13b310be0f9223466c529ca18f
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67312906"
---
# <a name="intellisense-completion-for-unimported-types"></a>針對未匯入的型別完成 IntelliSense

此重構適用於：

- C#

**功能：** IntelliSense 針對未匯入的型別提供完成。

**時機：** 您想要新增專案中已經有相依性的型別，但匯入陳述式尚未新增至您的檔案。 

**原因：** 您不需要將匯入陳述式手動新增至您的檔案。

## <a name="how-to"></a>操作說明

1. 在您開始使用專案中已經有相依性的型別時，IntelliSense 將會提供建議。
2. 按 **Tab**。 

   匯入陳述式將會新增至您的檔案。

   ![針對未匯入的型別完成 IntelliSense](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
