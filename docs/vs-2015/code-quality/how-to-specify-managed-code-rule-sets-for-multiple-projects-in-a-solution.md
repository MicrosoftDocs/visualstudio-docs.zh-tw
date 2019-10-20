---
title: 如何：在方案中指定多個專案的 Managed 程式碼規則集 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656415"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>如何：對方案中的多個專案指定 Managed 程式碼規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

根據預設，解決方案的所有 managed 專案都會被指派 Microsoft 最低建議規則程式碼分析*規則集*。 您可以在方案的 [屬性] 對話方塊中，變更指派給方案專案的規則集。

> [!NOTE]
> 根據預設，專案程式碼分析不會做為組建步驟執行。 若要啟用程式碼分析做為組建步驟，請參閱[如何：針對 Managed 程式碼專案設定程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)。

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>若要在 managed 程式碼方案中指定多個專案的規則集

1. 在 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]。 在 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] 或 [!INCLUDE[vsPro](../includes/vspro-md.md)] 中開啟方案。

2. 在 [**分析**] 功能表上，按一下 [**設定方案的程式碼分析**]。

3. 如有必要，請展開 [**通用屬性**]，然後按一下 [程式**代碼分析設定**]。

4. 您可以指定一個或多個專案的規則集。

    - 若要為個別專案指定規則集，請按一下專案名稱。

    - 若要為多個專案指定規則集，請按住 CTRL 鍵，然後按一下專案名稱。

    - 若要指定方案中的所有專案，請按住 SHIFT 鍵，然後按一下專案清單。

5. 按一下專案的 [**規則集**] 欄位，然後按一下您要套用之規則集的名稱。
