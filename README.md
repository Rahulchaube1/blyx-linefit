<img src="assets/logo.png" width="112" height="112" alt="LineFit logo">

# LineFit

Compute the usable print area and whole lines per page. This Blyx library is part of the documents, images and media collection.

A report can fit in aggregate yet overflow when a paragraph must stay together. Pack the measured paragraphs into the usable page area. [W3C, CSS fragmentation](https://www.w3.org/TR/css-break-3/)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-linefit.git
cd blyx-linefit
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-linefit) · [Package page](https://www.blyx-lang.space/packages/linefit) · [Handbook](https://doc.blyx-lang.space/guide/lapwing)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-linefit.git vendor/linefit
```

```blyx
use vendor::linefit::linefit;

fn main() {
    let paper = 100.0;
    let top = 10.0;
    let bottom = 15.0;
    let line = 6.0;
    let result = linefit_capacity(paper, top, bottom, line);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
75
12
3
```

## API

`linefit_capacity(paper, top, bottom, line)`

Returns [usable height, whole-line capacity, residual height]. All dimensions use the same unit; a page with no usable height is invalid. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| paper | A positive finite number |
| top | A nonnegative finite number |
| bottom | A nonnegative finite number |
| line | A positive finite number |

## In use

[Lapwing](https://github.com/Rahulchaube1/blyx-lapwing) uses this module to preflight fixed-line document pagination with indivisible paragraphs.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-linefit/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The package artwork uses [Lucide icons](https://lucide.dev/license); see [artwork notices](assets/NOTICE.txt).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
