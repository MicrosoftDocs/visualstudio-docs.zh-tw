---
title: 為所有項目 (參數) 新增 Null 檢查
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74782304"
---
# <a name="add-null-checks-for-all-parameters"></a>為所有參數新增 Null 檢查 

此重構適用於： 

- C# 

**內容：** 創建並添加`if`語句，以檢查所有可取消檢查的空參數的 null。 

**何時：** 您希望快速添加所有適用方法參數的空檢查。

**原因：** 對許多參數編寫空檢查可能非常耗時且重複。 使用此重構功能既快速，又可讓程式更加健全。  

## <a name="how-to"></a>操作方式 

1. 將游標放在方法內的任何參數上。

2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。

   ![快速動作與重構](media/add-null-checks-for-all-parameters.png)
   
3. 選取**為所有參數新增 Null 檢查**的選項。

   ![為所有項目新增 Null 檢查](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>另請參閱 

- [Refactoring](../refactoring-in-visual-studio.md)
