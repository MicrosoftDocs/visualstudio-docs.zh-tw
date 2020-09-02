---
title: 如何：建立入門套件 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Starter Kits, creating
ms.assetid: ed7d1844-7c01-424a-a831-5003efe0f7bc
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f9df8d85c600cd383a9a9059e689e6cb9f232d8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668033"
---
# <a name="how-to-create-starter-kits"></a>如何：建立入門套件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

入門套件包含完整應用程式的程式碼，以及如何修改或擴充應用程式的文件。 建立入門套件基本上與建立標準專案範本相同，唯一的差異在於入門套件所包含的文件檔案設定為在建立根據入門套件的專案時開啟。

## <a name="designing-and-developing-a-starter-kit"></a>設計和開發入門套件
 首先，您必須識別想要開發的入門套件類型，並定義您的目標對象。 接下來，設計專案和文件以符合您的目標。

 如果您要建立範例應用程式或外掛程式：

- 建立可建置而不發生錯誤的專案。

- 新增範本程式碼來實作其他工作 (選擇性)。

- 準備文件。

  如果您要建立學習工具：

- 建立可建置而不發生錯誤的專案。

- 組織資源 (例如程式碼片段和項目範本)。

- 準備文件。

## <a name="creating-a-template"></a>建立範本
 在您完成專案和文件之後，就已準備好建立入門套件的專案範本。 此程序與建立專案範本完全相同。

 下列主題包含建立範本的相關資訊。

 [如何：建立專案範本](../ide/how-to-create-project-templates.md) 說明如何使用 [ **匯出範本** ] 建立範本。

 [如何：更新現有的範本](../ide/how-to-update-existing-templates.md) 說明如何編輯匯出的範本。 使用此程序即可修改 .vstemplate 檔案來自訂入門套件。

## <a name="see-also"></a>另請參閱
 [建立專案和專案範本](../ide/creating-project-and-item-templates.md)[自訂](../ide/customizing-project-and-item-templates.md)範本[Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
