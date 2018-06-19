---
title: 如何：隱藏所產生程式碼的程式碼分析警告
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac2c5d4a7aca3f77feabc0aaba75d7f56a751821
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919450"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>如何：隱藏所產生程式碼的程式碼分析警告
Managed 程式碼編譯器通常會產生程式碼加入至專案，以便快速的程式碼開發。 此外，開發人員通常會使用第三方工具可協助您快速地開發應用程式。 這些工具也會產生程式碼加入至專案。

 您可能想要查看產生的程式碼中發現的程式碼分析規則違規。 不過，您可能不想看到它們，如果您無法檢視及維護包含違規的程式碼。

 **隱藏來自產生的程式碼的結果**專案的程式碼分析屬性頁上的核取方塊可讓您選取您是否想要看到的協力廠商工具所產生的程式碼的程式碼分析警告。

> [!NOTE]
>  這個選項不會隱藏程式碼分析錯誤和警告，產生的程式碼時的錯誤和警告會出現在表單和範本。 您可以同時檢視及維護表單或範本的原始程式碼。

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>若要隱藏所產生的程式碼專案中的警告

1.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**屬性**。

2.  按一下**程式碼分析**。

3.  選取**隱藏來自產生的程式碼的結果**核取方塊。