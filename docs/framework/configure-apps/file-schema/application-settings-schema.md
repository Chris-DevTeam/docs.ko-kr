---
description: '자세히 알아보기: 응용 프로그램 설정 스키마'
title: 응용 프로그램 설정 스키마
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 24c5771e9d98d07bbdc8dab5fce0f1535bc9b582
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652902"
---
# <a name="application-settings-schema"></a>응용 프로그램 설정 스키마

응용 프로그램 설정을 통해 Windows Forms 또는 ASP.NET 응용 프로그램에서 응용 프로그램 범위 및 사용자 범위 설정을 저장 하 고 검색할 수 있습니다. 이 컨텍스트에서 *설정은* 응용 프로그램 또는 현재 사용자와 관련 된 정보 이며, 데이터베이스 연결 문자열에서 사용자의 기본 설정 기본 창 크기에 이르기까지 모든 정보를 지정 합니다.

기본적으로 Windows Forms 응용 프로그램의 응용 프로그램 설정은 <xref:System.Configuration.LocalFileSettingsProvider> 클래스를 사용 합니다 .이 클래스는 .net 구성 시스템을 사용 하 여 설정을 XML 구성 파일에 저장 합니다. 응용 프로그램 설정에 사용 되는 파일에 대 한 자세한 내용은 [응용 프로그램 설정 아키텍처](/dotnet/desktop/winforms/advanced/application-settings-architecture)를 참조 하세요.

응용 프로그램 설정은 사용 하는 구성 파일의 일부로 다음 요소를 정의 합니다.

| 요소                    | 설명                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | **\<setting>** 응용 프로그램과 관련 된 모든 태그를 포함 합니다.                         |
| **\<userSettings>**        | **\<setting>** 현재 사용자와 관련 된 모든 태그를 포함 합니다.                        |
| **\<setting>**             | 설정을 정의합니다. 또는의 자식 **\<applicationSettings>** 입니다 **\<userSettings>** . |
| **\<value>**               | 설정 값을 정의 합니다. 의 자식 **\<setting>** 입니다.                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings> 요소

이 요소는 **\<setting>** 클라이언트 컴퓨터의 응용 프로그램 인스턴스와 관련 된 모든 태그를 포함 합니다. 특성 없음을 정의합니다.

## <a name="usersettings-element"></a>\<userSettings> 요소

이 요소는 현재 응용 프로그램을 사용 하 고 있는 사용자에 해당 하는 모든 태그를 포함 **\<setting>** 합니다. 특성 없음을 정의합니다.

## <a name="setting-element"></a>\<setting> 요소

이 요소는 설정을 정의 합니다. 여기에는 다음과 같은 특성이 있습니다.

| attribute        | 설명 |
| ---------------- | ----------- |
| **name**         | 필수 사항입니다. 설정의 고유 ID입니다. Visual Studio를 통해 만든 설정은 이름으로 저장 됩니다 `ProjectName.Properties.Settings` . |
| **serializeAs** | 필수 사항입니다. 값을 텍스트로 직렬화 하는 데 사용할 형식입니다. 유효한 값은 다음과 같습니다.<br><br>- `string`. 값은을 사용 하 여 문자열로 serialize 됩니다 <xref:System.ComponentModel.TypeConverter> .<br>- `xml`. 값은 XML 직렬화를 사용 하 여 serialize 됩니다.<br>- `binary`. 이 값은 이진 serialization을 사용 하 여 텍스트 인코딩 이진으로 serialize 됩니다.<br />- `custom`. 설정 공급자는이 설정에 대 한 기본적인 지식을 갖고 있으며 직렬화 및 역직렬화 합니다. |

## <a name="value-element"></a>\<value> 요소

이 요소는 설정 값을 포함 합니다.

## <a name="example"></a>예제

다음 예제에서는 두 개의 응용 프로그램 범위 설정 및 두 개의 사용자 범위 설정을 정의 하는 응용 프로그램 설정 파일을 보여 줍니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a>참고 항목

- [애플리케이션 설정 개요](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [애플리케이션 설정 아키텍처](/dotnet/desktop/winforms/advanced/application-settings-architecture)
