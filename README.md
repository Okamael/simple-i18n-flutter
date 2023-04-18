# Implementando I18N com flutter


Nos casos onde usuarios de diferentes linguas irão acessar seu aplicativo, é interessante
que o aplicativo esteja na linguagem que o usuario usa, nisso entra a Intercionalização com o padrão I18

#Como implementar em aplicações flutter.

Com o projeto já é necessario adicionar os seguintes pacotes, há duas formas para isso

por linha de comando no terminal exemplo a baixo:
``` flutter pub add flutter_localizations --sdk=flutter 
 flutter pub add intl:any
```

Ou adicionando a seguinte tag no pubspec.yaml

![pubspec](https://user-images.githubusercontent.com/46298240/232896597-e20488ab-6600-4329-843a-8b3601b6fd67.jpg)

Ainda dentro do Spec adicionage a tag de generate na sessão flutter

![habilitando generate](https://user-images.githubusercontent.com/46298240/232896699-a78182bb-49ef-4ca2-bfa8-3a5c9fd31dd1.jpg)

Na Raiz do projeto crie um arquivo chamado `l10n.yaml` ele é responsavel pelas configurações a onde ira ser encontrado as localizações.
Contendo o seguinte conteudo.
```
arb-dir: lib/l10n
template-arb-file: app_pt.arb
output-localization-file: app_localizations.dart
```

arb-dir: diretorio a onde esta localizado os arquivos .arb
template-arb-file: template padrão configurado para o pt-br
output-localization-file: class gerada com as palavras cadastradas.

Crie uma pasta na Lib/l10n e crie os arquivos 

![image](https://user-images.githubusercontent.com/46298240/232898891-ad973981-0413-49c2-8e69-0f382065df38.png)

o conteudo deles seguem o formado json 
```json
{
    "helloWorld":"Ola mundo"
}
```

## Utilizando no app

Crie uma class que instancia o MaterialApp

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Sample App Localização',
        localizationsDelegates: [
          AppLocalizations.delegate,
          GlobalMaterialLocalizations.delegate,
          GlobalCupertinoLocalizations.delegate,
          GlobalWidgetsLocalizations.delegate
        ],
        supportedLocales: [
          Locale('en'),
          Locale('pt', 'BR'),
          Locale('es'),
        ],
        home: MyHomeApp());
  }
}
```

para usar basta adicionar AppLocalizations.of(context)!.{DO METODO}
![image](https://user-images.githubusercontent.com/46298240/232899543-c251b848-f7dc-430c-9908-26a2f73d8477.png)

```dart
class MyHomeApp extends StatelessWidget {
  const MyHomeApp({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(AppLocalizations.of(context)!.helloWorld),
      ),
      body: Center(
        child: TextButton(
          onPressed: () {},
          child: Text(AppLocalizations.of(context)!.helloWorld),
        ),
      ),
    );
  }
}

```



https://user-images.githubusercontent.com/46298240/232900044-d7553473-cf8a-4b5d-bc5b-c0bbfec7b455.mp4



