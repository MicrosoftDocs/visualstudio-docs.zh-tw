---
title: 如何：啟用和停用 Managed 程式碼的自動程式碼分析
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6786d3f93c1ab7026c8a6bde25f5c43cb999e08a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>如何： 啟用和停用自動程式碼分析，managed 程式碼

您可以設定程式碼分析 managed 程式碼專案的每次建置之後執行。 您可以設定不同的程式碼分析屬性，每個組建組態。

## <a name="to-enable-or-disable-automatic-code-analysis"></a>若要啟用或停用自動程式碼分析

1. 在**方案總管 中**，以滑鼠右鍵按一下專案，然後選擇**屬性**。

1. 在 內容 對話方塊中的 專案，選擇 **程式碼分析**。

1. 指定組建類型中的**組態**與目標平台的**平台**。

1. 若要啟用或停用自動程式碼分析，請選取或清除**建置時啟用程式碼分析**核取方塊。
