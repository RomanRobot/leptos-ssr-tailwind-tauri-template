# Tailwind-Leptos-Tauri Template

Simple template to use SSR leptos with Tauri for iOS, Android, Windows, Mac, Linux and Web.

To get started just use [cargo generate](https://crates.io/crates/cargo-generate) with this repo.

```bash
cargo generate --git https://github.com/Alt-iOS/tailwind-leptos-tauri-template.git
```

Thanks to the Leptos and Tauri teams for the amazing work.
Also all credit to [sjud](https://github.com/sjud/leptos_tauri_from_scratch/tree/main) and [Krzysztof](https://gitlab.com/cristofa/tauri-leptos-template) for their examples, as they were the base for this template.

This project differs as it:

- Adds Tailwind to sjud's example
- Adds SSR to Krzysztof
- Separates the server from the frontend crate
- Separated the app module from the frontend crate
- Separated the backend logic from the rest

## Structure
- `/app/` - UI section
- `/frontend/` - launch point for the hydration/csr
- `/backend/` - server logic and server functions
- `/server/` - the launch point of the axum server
- `/src-tauri/` - Tauri related settings, build script

## Test everything is working

### Prerequisites
#### 1. Tauri CLI
> See if Tauri CLI is installed:
> ```
> cargo tauri --version
> ```
Install Tauri CLI:
```bash
cargo install tauri-cli
```

#### 2. Leptos CLI
> See if Leptos CLI is installed:
> ```
> cargo leptos --version
> ```
Install Leptos CLI:  
`cargo-leptos` has a dependency on `openssl-sys` that requires Perl to compile.
1. Download portable Strawberry Perl from https://strawberryperl.com/
1. Extract it
1. Run `portableshell.bat`
1. From that shell go to this project directory
1. Install Leptos CLI using
```bash
cargo install cargo-leptos
```

#### 3. wasm32-unknown-unknown target
> See if the target is installed:
> ```bash
> rustup target list --installed
> ```
Install the target:
```bash
rustup target add wasm32-unknown-unknown
```

### Launch native app
```bash
cargo tauri dev
```

### Serve web app
```bash
cargo leptos watch
```

## How To
### Update wasm-bindgen version
```
cargo update -p wasm-bindgen --precise <version>
```
Recompile frontend:
```
cd frontend
cargo clean
cargo leptos build
```

## Mobile dev
`cargo tauri android init && cargo tauri ios init`

- iOS requires a mac and XCode
- Android requires JVM 17 or modifying the gradle version.
  You can change it in the distributionUrl and for compatibility [check](https://docs.gradle.org/current/userguide/compatibility.html)
