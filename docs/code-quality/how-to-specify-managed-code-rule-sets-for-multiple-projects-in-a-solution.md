---
title: "如何： 個方案中的多個專案指定 Managed 程式碼規則集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e0b6a2864340f87702b765f49605ebdb3aaa555c
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2018
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>如何：對方案中的多個專案指定 Managed 程式碼規則集

根據預設，方案的所有 managed 的專案都會被指派 Microsoft 最小建議規則程式碼分析*規則集*。 您可以變更規則集指派給專案的方案的 [屬性] 對話方塊中的解決方案。

> [!NOTE]
> 根據預設，專案程式碼分析不會以建置步驟執行。 若要啟用程式碼分析做為建置步驟，請參閱[How to： 設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)。

1. 在 Visual Studio 中開啟方案。

2. 在**分析**功能表上，按一下 **設定方案的程式碼分析**。

3. 如果有必要，請展開**通用屬性**，然後按一下 **程式碼分析設定**。

4. 您可以指定規則集的一個或多個專案。

    - 若要指定個別的專案中設定的規則，請按一下專案名稱。

    - 若要指定規則集的多個專案，請按住 ctrl 鍵並按一下 專案名稱。

    - 若要指定的所有專案方案中，按住 shift 鍵並按一下清單中的專案。

5. 按一下**規則集**欄位的專案，然後按一下您想要套用的規則的名稱設定。