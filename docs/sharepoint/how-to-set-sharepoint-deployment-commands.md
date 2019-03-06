---
title: HOW TO：設定 SharePoint 部署命令 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 79843389adcd7dc0a4e350e4fd010d450c837a4e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606683"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>HOW TO：設定 SharePoint 部署命令
  您可以自訂部署程序，藉由設定預先部署和部署後命令。 當您偵錯 SharePoint 方案，從 Visual Studio 時，這些命令會執行之前和之後的其他部署動作。

### <a name="to-add-a-pre-deployment-command"></a>若要將預先部署命令

1.  在功能表列上選擇 **專案** > **\<*ProjectName*> 屬性**。

2.  選擇**SharePoint**  索引標籤。

3.  在 **預先部署命令列**文字中，輸入 MS-DOS 或 MSBuild 命令，以自訂此步驟。

     例如，若要完成部署之前，請列出目錄內容，請輸入**dir**。

### <a name="to-add-a-post-deployment-command"></a>若要加入部署後命令

1.  在功能表列上選擇 **專案** > **\<*ProjectName*> 屬性**。

2.  選擇**SharePoint**  索引標籤。

3.  在 **部署後命令列**文字中，輸入 MS-DOS 或 MSBuild 命令，以自訂此步驟。

     例如，若要完成部署之後，請列出目錄內容，請輸入**dir**。 若要使用 MSBuild 變數，複製 [build] 目錄中的組件，請輸入**複製 $ （targetpath) c:\DeploymentDirectory**。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
