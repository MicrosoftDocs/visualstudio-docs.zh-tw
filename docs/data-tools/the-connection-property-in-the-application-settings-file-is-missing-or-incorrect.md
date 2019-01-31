---
title: 應用程式設定檔中的連接屬性遺漏或不正確
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 77724510-ff59-4d43-b933-a0434e1ac597
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: d125c5e12320f0c2a17e12c53ca62764f4dfe79f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070810"
---
# <a name="the-connection-property-in-the-application-settings-file-is-missing-or-incorrect"></a>應用程式設定檔中的連接屬性遺漏或不正確

應用程式設定檔案中的連接屬性遺漏或不正確。 改用來自 *.dbml* 檔案的連接字串代替。

*.dbml* 檔案包含對應用程式設定檔中無法找到之連接字串的參考。 這是告知性訊息，當您按一下 [確定] 時就會建立連接字串設定。

若要回應這個訊息，請選取**確定**。 *.dbml* 檔案中所含的連線資訊會新增至應用程式設定。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)