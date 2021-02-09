---
title: 在 ClickOnce 應用程式中包含資料檔案
description: 瞭解如何將任何類型的資料檔案新增至 ClickOnce 應用程式，以儲存在目的地電腦本機磁片上的資料目錄中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f4b5e8fe9d17a6de9abac2681074dcfc162e9b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900610"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>如何：在 ClickOnce 應用程式中包含資料檔案
您安裝的每個 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式都會被指派目的地電腦本機磁片上的資料目錄，應用程式可以在其中管理本身的資料。 資料檔案可包含任何類型的檔案：文字檔、XML 檔案，或甚至是 Microsoft Access 資料庫 (*.mdb*) 檔。 下列程式示範如何將任何類型的資料檔案加入至您的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。

### <a name="to-include-a-data-file-by-using-mageexe"></a>使用 Mage.exe 來包含資料檔案

1. 將資料檔案新增至應用程式目錄，並包含應用程式的其餘部分。

    一般而言，您的應用程式目錄會是標示為部署目前版本的目錄，例如1.0.0.0 版。

2. 更新您的應用程式資訊清單，以列出資料檔案。

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    執行此工作會重新建立應用程式資訊清單中的檔案清單，也會自動產生雜湊簽章。

3. 在您慣用的文字或 XML 編輯器中開啟應用程式資訊清單，並尋找最近新增之檔案的專案 `file` 。

    如果您已新增名為的 XML 檔案 `Data.xml` ，檔案看起來會像下面的程式碼範例。

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. 將屬性加入 `type` 至這個專案，並提供其值 `data` 。

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. 使用您的金鑰組或憑證重新簽署應用程式資訊清單，然後重新簽署部署資訊清單。

    您必須重新簽署部署資訊清單，因為它的應用程式資訊清單雜湊已變更。

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>使用 MageUI.exe 來包含資料檔案

1. 將資料檔案新增至應用程式目錄，並包含應用程式的其餘部分。

2. 一般而言，您的應用程式目錄會是標示為部署目前版本的目錄，例如1.0.0.0 版。

3. **在 [檔案**] 功能表上，按一下 [**開啟**] 以開啟您的應用程式資訊清單。

4. 選取 [ **檔案** ] 索引標籤。

5. 在索引標籤頂端的文字方塊中，輸入包含您應用程式檔案的目錄，然後按一下 [ **填入**]。

     資料檔案將會出現在方格中。

6. 將資料檔案的 **檔案類型** 值設定為 [ **資料**]。

7. 儲存應用程式資訊清單，然後重新簽署檔案。

     *MageUI.exe* 會提示您重新簽署檔案。

8. 重新簽署部署資訊清單

     您必須重新簽署部署資訊清單，因為它的應用程式資訊清單雜湊已變更。

## <a name="see-also"></a>另請參閱
- [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)