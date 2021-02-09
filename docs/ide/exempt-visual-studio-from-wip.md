---
title: 免於套用 Windows 資訊保護
description: 瞭解從 Windows 資訊保護排除 Visual Studio，同時仍然允許它使用企業資料。
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ff233b959b4ad691646c5e47c659b398b283b5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898004"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>設定 Visual Studio 作為 WIP 豁免應用程式

[Windows 資訊保護](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (WIP) 可協助保護企業資料，使其不會從電子郵件、社交媒體和公用雲端之類不受企業控管的應用程式外洩。 WIP 可協助避免企業擁有的裝置與個人裝置發生意外的資料外洩情況，而且不需要變更環境或其他應用程式。

已啟用 WIP 的應用程式應該會防止企業資料移至未受保護的網路位置，以及避免加密個人資料。 Visual Studio 不是已啟用的應用程式，因此除非您免除它，否則它並不適用於已啟用 WIP 的環境。 請遵循本文中的步驟來啟用 Visual Studio，以便在已啟用 WIP 的電腦上運作。

## <a name="configure-vs-as-a-wip-exempt-app"></a>設定 VS 作為 WIP 豁免應用程式

您可以讓 Visual Studio 免於套用 WIP 限制，但仍然允許它使用企業資料。 WIP 豁免應用程式可以使用 IP 位址或主機名稱連線到企業雲端資源。 不會套用任何加密，且應用程式可以存取本機檔案。

若要讓 Visual Studio 免於套用 WIP，請遵循[豁免傳統型應用程式的步驟](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy)。

## <a name="create-a-wip-exempt-applocker-policy-file"></a>建立 WIP 豁免 AppLocker 原則檔

由於 Visual Studio 包含多個二進位檔，因此請[建立 WIP 豁免 AppLocker 原則檔](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard)。 AppLocker 可讓您針對某個資料夾內的所有檔案自動產生規則。

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>將 AppCompat 新增至企業雲端資源原則

若要指定 Visual Studio 可以存取您網路上企業資料的位置，請遵循這些[定義受保護應用程式可在其中尋找並傳送企業資料之位置的步驟](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data)。 若要停止 Windows 透過 IP 位址封鎖雲端資源的連線，請務必將 /\*AppCompat\*/ 字串新增至設定。

## <a name="see-also"></a>另請參閱

- [使用 WIP 的應用程式行為](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
