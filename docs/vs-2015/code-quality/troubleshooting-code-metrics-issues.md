---
title: 針對程式碼度量問題進行疑難排解 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4d374a2737e2ce8892304b615bebcf99d9c60ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672459"
---
# <a name="troubleshooting-code-metrics-issues"></a>程式碼度量問題疑難排解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

收集程式碼度量時，可能會遇到下列一些問題：

- [Visual Studio 2010 程式碼複雜度計算變更](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="changes-in-visual-studio-2010-code-complexity-calculations"></a><a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Visual Studio 2010 程式碼複雜度計算的變更
 針對相同的函式，在下列情況下，[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 中所計算的程式碼複雜度度量可以與舊版 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 所計算的度量不同：

- 此函式包含一或多個 catch 區塊。 在舊版 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 中，計算時不會包含 catch 區塊。 在 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 中，每個 catch 區塊的複雜度都會新增至函式的複雜度。

- 函式包含參數 (VB 中的 Select Case) 陳述式。 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 與舊版本之間的編譯器差異可能會針對一些包含 fallthrough 案例的 switch 陳述式產生不同的 MSIL 程式碼。

## <a name="see-also"></a>另請參閱
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
