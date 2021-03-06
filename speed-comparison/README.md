Speed comparison of the three DI libraries Katana, [Koin](https://github.com/Ekito/koin) and [Kodein](https://github.com/Kodein-Framework/Kodein-DI).

Also see this independent [comparison](https://github.com/Sloy/android-dependency-injection-performance).

## Test setup

Please have a look at the source code. The test is divided into the two blocks *setup* and *execution*. *Setup* tests 
how fast the test subject is in setting up the dependency injection (creating modules, bindings, etc.) and *execution*
tests the actual injection. The test collects the average and median time in nanoseconds of 1,000,000 iterations of
each block.

### Library versions

| Library | Version |
| ------- | ------- |
| Katana  | 1.2.0   |
| Koin    | 1.0.2   |
| Kodein  | 6.0.1   |

For fairness towards Kodein the [erased](http://kodein.org/Kodein-DI/?5.2/getting-started#_flavour) version of Kodein
was used for this comparison. It should be faster since it doesn't use reflection.

## Test environment

The test has been performed on a 2017 MacBook Pro with a 3,1 GHz Intel Core i7 CPU, 16 GB RAM, macOS Mojave 10.14 and
Java 1.8.0_181-b13.

## Results

All times in nanoseconds.

| Library | Setup (average) | Setup (median) | Execution (average) | Execution (median) |
| ------- | ---------------:| --------------:| -------------------:| ------------------:|
| Katana  |     1026.766894 |          766.0 |          355.977582 |              276.0 |
| Kodein  |     1621.426234 |         1149.0 |          970.987781 |              729.0 |
| Koin    |     5155.923505 |         3968.0 |         7035.575007 |             5653.0 |

## How to build and run comparison

From the root folder of the project run:

```
./gradlew :speed-comparison:build
java -jar ./speed-comparison/build/libs/speed-comparison-fat-1.2.0.jar
```
