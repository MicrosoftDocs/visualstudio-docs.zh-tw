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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74782304"
---
# <a name="add-null-checks-for-all-parameters"></a>為所有參數新增 Null 檢查 

此重構適用於： 

- C# 

**功能：** 建立並加入 `if` 語句，以檢查所有可為 null、非 checked 參數的 nullity。 

時機 **：** 您想要針對所有適用的方法參數快速新增 null 檢查。

**原因：** 針對許多參數寫入 null 檢查可能會很耗時且重複。 使用此重構功能既快速，又可讓程式更加健全。  

## <a name="how-to"></a>操作說明 

1. 將游標放在方法內的任何參數上。

2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構] 功能表。

   ![快速動作與重構](media/add-null-checks-for-all-parameters.png)
   
3. 選取**為所有參數新增 Null 檢查**的選項。

   ![為所有項目新增 Null 檢查](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>請參閱 

- [重構](../refactoring-in-visual-studio.md)
