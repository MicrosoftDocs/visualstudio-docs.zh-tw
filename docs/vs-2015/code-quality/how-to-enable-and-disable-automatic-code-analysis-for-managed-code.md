---
title: 如何：啟用和停用 Managed 程式碼的自動程式碼分析 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d87cc57b31e63ae7aafa53c335df2b56f86a0409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658092"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>如何：啟用和停用 Managed 程式碼的自動程式碼分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以設定程式碼分析，在 managed 程式碼專案的每個組建之前執行。 您可以為每個設定設定不同的程式碼分析屬性 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 。

### <a name="to-enable-or-disable-automatic-code-analysis"></a>啟用或停用自動程式碼分析

1. 在 **方案總管**中，以滑鼠右鍵按一下專案，然後按一下 [ **屬性**]。

2. 在專案的 [屬性] 對話方塊中，按一下 [程式 **代碼分析**]。

3. 在 [**平臺**] 的 [設定] 和 [目標平臺 **] 中指定**組建類型。

4. 若要啟用或停用自動程式碼分析，請選取或清除 [ **在組建上啟用程式碼分析] (定義 CODE_ANALYSIS 常數) ** 核取方塊。
