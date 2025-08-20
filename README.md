# Conversor de Moedas — Kotlin + Compose (PTAX)

App Android para converter valores entre **BRL, USD, EUR, ARS e GBP** usando **PTAX** do Banco Central do Brasil.

## Stack

* **Kotlin 2.x** + **Jetpack Compose (Material 3)**
* **OkHttp** para HTTP
* **ViewModel + StateFlow**
* Min SDK 24, JVM 17

## Como executar

1. Abra no Android Studio.
2. Garanta os repositórios em `settings.gradle.kts`: `google()`, `mavenCentral()`, `gradlePluginPortal()`.
3. Em `build.gradle.kts` (raiz):

   ```kotlin
   plugins {
     id("com.android.application") version "8.6.1" apply false
     id("org.jetbrains.kotlin.android") version "2.0.21" apply false
     id("org.jetbrains.kotlin.plugin.compose") version "2.0.21" apply false
   }
   ```
4. Em `app/build.gradle.kts`:

   ```kotlin
   plugins { id("com.android.application"); id("org.jetbrains.kotlin.android"); id("org.jetbrains.kotlin.plugin.compose") }
   buildFeatures { compose = true }
   ```

   > Com Kotlin 2.x **não** use `composeOptions { kotlinCompilerExtensionVersion = ... }`.
5. `AndroidManifest.xml`:

   ```xml
   <uses-permission android:name="android.permission.INTERNET"/>
   ```
6. Execute no emulador/dispositivo.

## API utilizada

**PTAX — Olinda (OData) / Banco Central do Brasil**
Endpoint:

```
https://olinda.bcb.gov.br/olinda/servico/PTAX/versao/v1/odata/
CotacaoMoedaDia(moeda=@moeda,dataCotacao=@dataCotacao)?
@moeda='<CODIGO>'&@dataCotacao='<MM-dd-YYYY>'&$top=1&$format=json
```

Campos usados: `cotacaoCompra`, `cotacaoVenda`.

## Estrutura

```
app/src/main/
 ├─ AndroidManifest.xml
 ├─ java/com/example/conversordemoedas/
 │   ├─ MainActivity.kt
 │   ├─ CurrencyViewModel.kt
 │   └─ ExchangeRepository.kt
 └─ res/values/ (strings.xml, themes.xml)
``` 
