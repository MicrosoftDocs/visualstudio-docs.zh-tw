---
title: 將匿名型別轉換為元組
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f7e89c5b5a05900fe42af62ef87f70292e94e662
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094270"
---
# <a name="convert-anonymous-type-to-tuple"></a>將匿名型別轉換為元組

此重構適用於：

- C#

- Visual Basic

事項 **：** 將匿名型別轉換為元組。

時機 **：** 您有一個限定為元組的匿名型別。

**原因：** [元組](/dotnet/csharp/tuples) 有助於將您的語法保持輕量。 這個快速動作讓這項 C# 功能運用上更加輕鬆。

## <a name="how-to"></a>操作方式

1. 將游標放在匿名型別中。
2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。

   ![將匿名型別轉換為元組](media/convert-anon-to-tuple.png)

2. 按 **Enter** 鍵接受重構。

   ![將匿名型別轉換為元組](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
