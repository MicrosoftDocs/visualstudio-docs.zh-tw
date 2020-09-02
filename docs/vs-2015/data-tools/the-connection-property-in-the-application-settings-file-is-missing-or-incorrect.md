---
title: 應用程式佈建檔案中的連接屬性遺漏或不正確 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 77724510-ff59-4d43-b933-a0434e1ac597
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b51ff1b20f197de5b6773413558b7e71764780b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655409"
---
# <a name="the-connection-property-in-the-application-settings-file-is-missing-or-incorrect"></a>應用程式設定檔中的連接屬性遺漏或不正確
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

應用程式設定檔案中的連接屬性遺漏或不正確。 改用來自 .dbml 檔案的連接字串代替。

 .dbml 檔案參考了應用程式設定檔案中所沒有的連接字串。 這是告知性訊息，當您按一下 [確定]**** 時就會建立連接字串設定。

### <a name="to-respond-to-this-message"></a>若要回應這個訊息

- 按一下 [確定]  。 .dbml 檔案中所含的連接資訊會加入至應用程式設定。

## <a name="see-also"></a>另請參閱
 [LINQ to SQL 工具 Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [逐步解說：建立 LINQ to SQL 類別 (O-R 設計工具) ](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [鋼筆：如何：新增或移除應用程式設定](https://msdn.microsoft.com/a233965c-126d-46ab-add4-efb758f576f4) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
