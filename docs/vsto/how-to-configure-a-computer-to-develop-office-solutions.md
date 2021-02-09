---
title: 如何：設定電腦以開發 Office 方案
description: 瞭解如何設定開發電腦，讓您可以使用 Visual Studio 中的 Microsoft Office 開發人員工具。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eeb5deffd0d6dbfb39da22db993bdb201bac5e17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913485"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>如何：設定電腦以開發 Office 方案
  若要設定開發電腦，讓您可以使用 Visual Studio 中的 Microsoft Office Developer Tools，請遵循本主題中的指示。 您必須擁有開發電腦上的系統管理權限，才能執行這些步驟。

### <a name="to-configure-the-development-computer"></a>設定開發電腦

1. 安裝包含 Office Developer Tools 的 Visual Studio 版本。 預設會安裝 Office Developer Tools。 如果您選取要安裝的功能來自訂 Visual Studio 安裝，請確定已在安裝期間選取 **Microsoft Office 開發人員工具** 。 如需包含 Office developer tools 之 Visual Studio 版本的詳細資訊，請參閱 [設定電腦以開發 office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)。

2. 安裝由 Visual Studio 中 Office Developer Tools 支援的 Office 版本。 如需詳細資訊，請參閱 [設定電腦以開發 Office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)。

     請確定您也針對所安裝的 Office 版本安裝 PIA。 PIA 預設會與 Office 一起安裝。 如果您修改 Office 安裝程式，請確定已針對您要設為目標的應用程式選取 [.Net 程式設計 **支援** ] 功能。

3. 如果您有英文版的 Visual Studio 但使用非英文版的 Windows 設定，您可以安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 語言套件，查看與 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] windows 相同語言的訊息。 非英文版的 Visual Studio 會自動安裝語言套件。 您可以從 [Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=54246)取得語言套件。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio&#41;中開始 &#40;Office 開發 ](../vsto/getting-started-office-development-in-visual-studio.md)
- [如何：安裝 Visual Studio Tools for Office 執行時間可轉散發套件](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [如何：安裝 Office 主要 interop 元件](../vsto/how-to-install-office-primary-interop-assemblies.md)
