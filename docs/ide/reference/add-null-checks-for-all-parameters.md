---
title: 為所有項目 (參數) 新增 Null 檢查
ms.date: 07/24/2019
ms.topic: reference
author: stcahlon
ms.author: t-shzach
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: da3a616844dbe914cfe796ec35d1501bf83dd1ef
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712730"
---
# <a name="add-null-checks-for-all-parameters"></a>為所有參數新增 Null 檢查 

此重構適用於： 

- C# 

**功能：** 建立並新增 `if` 陳述式來檢查所有可為 Null 之非檢查參數的 Null 狀態。 

**時機：** 您想要快速地為所有適用的方法參數新增 Null 檢查。

**原因：** 為許多參數撰寫 Null 檢查可能相當耗時且需重複操作。 使用此重構功能既快速，又可讓程式更加健全。  

## <a name="how-to"></a>操作說明 

1. 將游標放在方法內的任何參數上。

2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構]  功能表。

   ![快速動作與重構](media/add-null-checks-for-all-parameters.png)
   
3. 選取**為所有參數新增 Null 檢查**的選項。

   ![為所有項目新增 Null 檢查](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>另請參閱 

- [重構](../refactoring-in-visual-studio.md) 
