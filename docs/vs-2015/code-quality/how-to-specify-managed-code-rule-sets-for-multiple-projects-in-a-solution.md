---
title: HOW TO：個方案中的多個專案指定 Managed 程式碼規則集 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2bf83c66f86d516d18221d01470e125979d39349
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939234"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>HOW TO：在方案中的多個專案指定 Managed 程式碼規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

根據預設，所有 managed 的專案的方案指派 Microsoft 最小建議規則程式碼分析*規則集*。 您可以變更指派給在解決方案的 [屬性] 對話方塊中的方案專案規則集。  
  
> [!NOTE]
>  根據預設，專案程式碼分析不會做為建置步驟執行。 若要啟用程式碼分析做為建置步驟，請參閱[How to:設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)。  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>若要指定的規則集在 managed 程式碼解決方案中的多個專案  
  
1.  在  [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]。 在 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] 或 [!INCLUDE[vsPro](../includes/vspro-md.md)] 中開啟方案。  
  
2.  在上**分析** 功能表中，按一下**設定為方案的程式碼分析**。  
  
3.  如果有必要，請依序展開**通用屬性**，然後按一下**程式碼分析設定**。  
  
4.  您可以指定一個或多個專案設定的規則。  
  
    -   若要指定為個別的專案設定的規則，按一下 專案名稱。  
  
    -   若要指定規則集的多個專案，請按住 ctrl 鍵並按一下 專案名稱。  
  
    -   若要在方案中指定的所有專案，請按住 SHIFT 並按一下 [專案] 清單中。  
  
5.  按一下 **規則集**欄位的專案，然後按一下您想要套用的規則的名稱設定。
