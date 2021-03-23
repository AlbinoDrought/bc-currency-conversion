# Currency Conversion for GNU bc

Combine GNU units with GNU bc

## Requirements

- [GNU units](https://www.gnu.org/software/units/)
- [GNU bc](https://www.gnu.org/software/bc/)

## Usage

### Generating Script

`gen.sh` creates a bc-compatible script based on the configured currencies. You need to pass the output of it to `bc`.

Oneliner:

```sh
{ ./gen.sh; cat } | bc -li
```

Twoliner:

```sh
./gen.sh > conversion.bc
bc -l conversion.bc
```

### Converting Currencies

Once the script is loaded, the conversion functions can be used like:

```bc
usd2cad(1)
1.2721644

cad2usd(10)
7.86061910

usd2eur(10)
8.25120920

usd2eur(cad2usd(gbp2cad(10)))
11.24751946386381953707
```

### More Currencies

Add them to the `currencies` array in [`gen.sh`](./gen.sh)

### Updating Rates

If your currency conversion rates are out of date, try running `units_cur` as root: https://www.gnu.org/software/units/manual/html_node/Currency.html
