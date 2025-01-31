![Maintained YES](https://img.shields.io/badge/Maintained%3F-yes-green.svg)
![Delphi Supported Versions](https://img.shields.io/badge/Delphi%20Supported%20Versions-XE%20and%20ever-blue.svg)
![Platforms](https://img.shields.io/badge/Platforms-Win32%20and%20Win64-red.svg)
![Compatibility](https://img.shields.io/badge/Compatibility-VCL,%20Firemonkey,%20DataSnap%20-brightgreen.svg)

# IPGeoLocation

Biblioteca de geolocalização por IP.

Implementa uma classe de abstração que recupera informações de geolocalização de um IP utilizando provedores de solução “IP-Geolocation”.

## O que é a geolocalização de IP?

A geolocalização baseada em endereços IP é uma técnica usada para estimar a localização geográfica de um dispositivo conectado à Internet usando o endereço IP do mesmo.  Este mecanismo depende de que o endereço IP do dispositivo apareça em um banco de dados com sua respectiva localização, endereço postal, cidade, país, região ou coordenadas geográficas, que são alguns dos níveis de detalhe que podem ser registrados.

Para mais informações: [Geolocalização de IPs](https://www.lacnic.net/3107/3/lacnic/geolocalizac%C3%A3o-de-ips)

## Para que?

Essa tecnologia é amplamente usada em:

* Geo Marketing
  * Propagandas direcionadas/sob medida
  * Informação interessante com base na localização
  * Promoções/campanhas destinadas a certo público/local
  * Empresas de turismo, companhias aéreas, redes hoteleiras
  * Entretenimento
  
* Direcionamento de conteúdo
  * Portais “globais” com conteúdos “locais”
  * Informações no idioma do leitor
  * Conteúdo de interesse local (notícia, novidades, etc)
  * Portais de notícias
  * Serviços de informação meteorológica
  * Serviços de emergência
  
* Controle de acesso (à conteúdos/serviços)
  * Restringir acesso conteúdo/serviços com base na “localização” do usuário
  * Conteúdos específicos para determinado “público”
  * Censura
  * Jogos online
  * Streaming vídeos/músicas

* Segurança
  * Restringir tráfego, por localização do usuário
  * Em situação de emergência/ataque descartar tráfego “não esperado”
  * Controle de SPAM
  * Firewalls

## Provedores Homologados

| Provedor | Site | API |
|---|---|---|
| IP2Location | https://www.ip2location.com | https://api.ip2location.com/v2 |
| IP Geolocation | https://ipgeolocation.io | https://api.ipgeolocation.io/ipgeo |
| IP Stack  | https://ipstack.com | http://api.ipstack.com |
| IP Ify | https://geo.ipify.org | https://geo.ipify.org/api/v1 |
| IP API | https://ipapi.com | http://api.ipapi.com/api |
| IP Info | https://ipinfo.io | https://ipinfo.io |
| IP Geolocation API | https://ipgeolocationapi.com | https://api.ipgeolocationapi.com/geolocate |
| IP Data | https://ipdata.co | https://api.ipdata.co |

## Demo
[![Download](https://img.shields.io/badge/Download-Demo.zip-orange.svg)](https://github.com/antoniojmsjr/IPGeoLocation/files/3775350/Demo.zip)

```delphi
uses IPGeoLocation, IPGeoLocation.Types;
```

```delphi
  try
     TIPGeoLocation
    .New
      .IP['177.97.112.28']
      .Provider[TTypeIPGeoLocationProvider.IPInfo]
        .Params
      .Request
        .Execute
        .ToJSON(ResultJSON); 
  except
    on E: EIPGeoLocationRequestException do
    begin
      var lMsg: string;
      lMsg := EmptyStr;
      lMsg := Concat(lMsg, Format('Provider: %s', [E.Provider]), sLineBreak);
      lMsg := Concat(lMsg, Format('Kind: %s', [IPGeoLocationExceptionKindToString(E.Kind)]), sLineBreak);
      lMsg := Concat(lMsg, Format('URL: %s', [E.URL]), sLineBreak);
      lMsg := Concat(lMsg, Format('Method: %s', [E.Method]), sLineBreak);
      lMsg := Concat(lMsg, Format('Status Code: %d', [E.StatusCode]), sLineBreak);
      lMsg := Concat(lMsg, Format('Status Text: %s', [E.StatusText]), sLineBreak);
      lMsg := Concat(lMsg, Format('Message: %s', [E.Message]), sLineBreak);

      Application.MessageBox(PWideChar(lMsg), 'ATENÇÃO', MB_OK + MB_ICONERROR);
    end;
    on E: Exception do
    begin
      Application.MessageBox(PWideChar(E.Message), 'ATENÇÃO', MB_OK + MB_ICONERROR);
    end;
  end;
```
![IP Geolocalização](https://user-images.githubusercontent.com/20980984/67627133-0e618680-f82d-11e9-9594-2d71a621daa4.png)

## Licença
[![License](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://github.com/antoniojmsjr/IPGeoLocation/blob/master/LICENSE)
