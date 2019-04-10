---
title: Mixing Functional Programming and Java
author: Hilco Wijbenga, xMatters
...

# Screen size

======================================================================================================================

                                               __  ____      _
                                              /  |/  (_)  __(_)___  ____ _
                                             / /|_/ / / |/_/ / __ \/ __ `/
                                            / /  / / />  </ / / / / /_/ /
                                           /_/  /_/_/_/|_/_/_/ /_/\__, /
                                                                 /____/
                                    ______                 __  _                   __
                                   / ____/_  ______  _____/ /_(_)___  ____  ____ _/ /
                                  / /_  / / / / __ \/ ___/ __/ / __ \/ __ \/ __ `/ /
                                 / __/ / /_/ / / / / /__/ /_/ / /_/ / / / / /_/ / /
                                /_/    \__,_/_/ /_/\___/\__/_/\____/_/ /_/\__,_/_/

                           ____                                                  _
                          / __ \_________  ____ __________ _____ ___  ____ ___  (_)___  ____ _
                         / /_/ / ___/ __ \/ __ `/ ___/ __ `/ __ `__ \/ __ `__ \/ / __ \/ __ `/
                        / ____/ /  / /_/ / /_/ / /  / /_/ / / / / / / / / / / / / / / / /_/ /
                       /_/   /_/   \____/\__, /_/   \__,_/_/ /_/ /_/_/ /_/ /_/_/_/ /_/\__, /
                                        /____/                                       /____/
                                                      __       __
                                     ____ _____  ____/ /      / /___ __   ______ _
                                    / __ `/ __ \/ __  /  __  / / __ `/ | / / __ `/
                                   / /_/ / / / / /_/ /  / /_/ / /_/ /| |/ / /_/ /
                                   \__,_/_/ /_/\__,_/   \____/\__,_/ |___/\__,_/

======================================================================================================================

# A simple function

```
f_x_r :: x -> r
```

# A simple function

```
f_x_y :: x -> y

g_y_z :: y -> z
```

# A simple function

```
f_x_y :: x -> y

g_y_z :: y -> z

h_x_z :: x -> z
h_x_z   v_x   =   g_y_z   (f_x_y   v_x)
```

# A simple function

```
f_x_y :: x -> y

g_y_z :: y -> z

h_x_z :: x -> z
h_x_z   v_x   =   g_y_z   (f_x_y   v_x)

(.) :: _        -> _        -> _ -> _
(.)   g   f   v_x   =   g   (f   v_x)
```

# A simple function

```
f_x_y :: x -> y

g_y_z :: y -> z

h_x_z :: x -> z
h_x_z   v_x   =   g_y_z   (f_x_y   v_x)

(.) :: _        -> _        -> _ -> z
(.)   g   f   v_x   =   g   (f   v_x)
```

# A simple function

```
f_x_y :: x -> y

g_y_z :: y -> z

h_x_z :: x -> z
h_x_z   v_x   =   g_y_z   (f_x_y   v_x)

(.) :: (y -> z) -> _        -> _ -> z
(.)   g   f   v_x   =   g   (f   v_x)
```

# A simple function

```
f_x_y :: x -> y

g_y_z :: y -> z

h_x_z :: x -> z
h_x_z   v_x   =   g_y_z   (f_x_y   v_x)

(.) :: (y -> z) -> (x -> y) -> _ -> z
(.)   g   f   v_x   =   g   (f   v_x)
```

# A simple function

```
f_x_y :: x -> y

g_y_z :: y -> z

h_x_z :: x -> z
h_x_z   v_x   =   g_y_z   (f_x_y   v_x)

(.) :: (y -> z) -> (x -> y) -> x -> z
(.)   g   f   v_x   =   g   (f   v_x)
```

# A simple function

```
f_x_y :: x -> y

g_y_z :: y -> z

h_x_z :: x -> z
h_x_z   v_x   =   (.)   g_y_z   f_x_y   v_x

(.) :: (y -> z) -> (x -> y) -> x -> z
(.)   g   f   v_x   =   g   (f   v_x)
```

# A simple function

```
f_x_y :: x -> y

g_y_z :: y -> z

h_x_z :: x -> z
h_x_z   v_x   =   (g_y_z   .   f_x_y)   v_x

(.) :: (y -> z) -> (x -> y) -> x -> z
(.)   g   f   v_x   =   g   (f   v_x)
```

# A simple function

```
f_x_y :: x -> y

g_y_z :: y -> z

h_x_z :: x -> z
h_x_z   =   g_y_z   .   f_x_y

(.) :: (y -> z) -> (x -> y) -> x -> z
(.)   g   f   v_x   =   g   (f   v_x)
```

# A simple function

```
f_x_r :: x -> r

(.) :: (y -> r) -> (x -> y) -> x -> r
(.)   g   f   v_x   =   g   (f   v_x)
```

# A simple function

```
f_x_r :: x -> r

(.) :: (y -> r) -> (x -> y) -> x -> r
(.)   g   f   v_x   =   g   (f   v_x)

identity :: x -> x
```

# A simple function

```
f_x_r :: x -> r

(.) :: (y -> r) -> (x -> y) -> x -> r
(.)   g   f   v_x   =   g   (f   v_x)

identity :: x -> x
identity   v_x   =   v_x
```

# A simple function

```
f_x_r :: x -> r
```

# A simple function

```
f_x_r :: x -> r

java.util.Function<X, R>
```

# A simple function

```
f_x_r :: x -> r

java.util.Function<X, R>

@FunctionalInterface
public interface MyFunction<X, R> {
    R apply(X v_x);
}
```

# A simple function

```
f_x_r :: x -> r

java.util.Function<X, R>

@FunctionalInterface
public interface MyFunction<X, R> {
    R apply(X v_x);
}

MyFunction<Integer, String> f = value_of_type_Integer -> String.valueOf(value_of_type_Integer);
```

# A simple function

```
f_x_r :: x -> r

java.util.Function<X, R>

@FunctionalInterface
public interface MyFunction<X, R> {
    R apply(X v_x);
}

MyFunction<Integer, String> f = value_of_type_Integer -> String.valueOf(value_of_type_Integer);

MyFunction<Integer, String> f = (final Integer value) -> String.valueOf(value);
```

# A simple function

```
f_x_r :: x -> r

java.util.Function<X, R>

@FunctionalInterface
public interface MyFunction<X, R> {
    R apply(X v_x);
}

MyFunction<Integer, String> f = value_of_type_Integer -> String.valueOf(value_of_type_Integer);

MyFunction<Integer, String> f = (final Integer value) -> String.valueOf(value);

MyFunction<Integer, String> f =                         String::valueOf;
```

# A simple function

```
f_x_r :: x -> r

java.util.Function<X, R>

@FunctionalInterface
public interface MyFunction<X, R> {
    R apply(X v_x);
}

MyFunction<Integer, String> f = value_of_type_Integer -> String.valueOf(value_of_type_Integer);

MyFunction<Integer, String> f = (final Integer value) -> String.valueOf(value);

MyFunction<Integer, String> f = String::valueOf;
```

# A slightly less simple function

```
f :: x ->  y ->  z -> r
```

# A slightly less simple function

```
f :: x ->  y ->  z -> r -- curried

f :: (x, y, z) -> r     -- uncurried
```

# A slightly less simple function

```
f :: x ->  y ->  z -> r
```

# A slightly less simple function

```
f :: x -> (y ->  z -> r)
```

# A slightly less simple function

```
f :: x -> (y -> (z -> r))
```

# A slightly less simple function

```
f :: x ->  y ->  z -> r
```

# A slightly less simple function

```
f :: x ->  y ->  z -> r

@FunctionalInterface
public interface Function3<X, Y, Z, R> {
    R apply(X v_x, Y v_y, Z v_z);
}
```

# A slightly less simple function

```
f :: x ->  y ->  z -> r

@FunctionalInterface
public interface Function3<X, Y, Z, R> {
    R apply(X v_x, Y v_y, Z v_z);
}

public static final <X, Y, Z, R> Function2<Y, Z, R> curry3(final Function3<X, Y, Z, R> function, final X v_x) {
    Objects.requireNonNull(function, "Missing 'function'.");
    return (v_y, v_z) -> function.apply(v_x, v_y, v_z);
}
```

# A slightly less simple function

```
f :: x ->  y ->  z -> r

@FunctionalInterface
public interface Function3<X, Y, Z, R> {
    R apply(X v_x, Y v_y, Z v_z);
}

public static final <X, Y, Z, R> Function2<Y, Z, R> curry3(final Function3<X, Y, Z, R> function, final X v_x) {
    Objects.requireNonNull(function, "Missing 'function'.");
    return (v_y, v_z) -> function.apply(v_x, v_y, v_z);
}

public static final <X, Y, R> Function1<Y, R> curry2(final Function2<X, Y, R> function, final X v_x) {
    Objects.requireNonNull(function, "Missing 'function'.");
    return v_y -> function.apply(v_x, v_y);
}
```

# Some useful types

The **Maybe** type can be used to indicate the lack of a value.

```
data Maybe x
    = Just x
    | Nothing
```

# Some useful types

The **Maybe** type can be used to indicate the lack of a value.

```
data Maybe x
    = Just x
    | Nothing
```

The **Result** type can be used to indicate that a function may fail to produce a value.

```
data Result error x
    = Success x
    | Failure error
```

# Some useful types

The **Maybe** type can be used to indicate the lack of a value.

```
data Maybe x
    = Just x
    | Nothing
```

The **Result** type can be used to indicate that a function may fail to produce a value.

```
data Result error x
    = Success x
    | Failure error
```

The **List** type can be used to indicate that a function may yield zero or more results.

```
data List x
    = Element x (List x)
    | Empty
```

# **Result error x** in Java

The **Result** type can be used to indicate that a function may fail to produce a value.

```
data Result error x
    = Success x
    | Failure error
```

# **Result error x** in Java

The **Result** type can be used to indicate that a function may fail to produce a value.

```
data Result error x
    = Success x
    | Failure error

public abstract class Result<X> {
    private Result() { }

    public static final class Success<X> extends Result<X> {
        public final X value;

        public Success(final X value) {
            Objects.requireNonNull(value, "Missing 'value'.");
            this.value = value;
        }
    }

    public static final class Failure<X> extends Result<X> {
        public final Exception exception;

        public Failure(final Exception exception) {
            Objects.requireNonNull(exception, "Missing 'exception'.");
            this.exception = exception;
        }
    }
}
```

# **Result error x** in Java

The **Result** type can be used to indicate that a function may fail to produce a value.

```
data Result error x
    = Success x
    | Failure error
```

# **Result error x** in Java

The **Result** type can be used to indicate that a function may fail to produce a value.

```
data Result error x
    = Success x
    | Failure error

f :: Result error x -> Text
f (Success v_x)      = "SUCCESS" -- v_x
f (Failure v_error)  = "FAILURE" -- v_error
```

# **Result error x** in Java

The **Result** type can be used to indicate that a function may fail to produce a value.

```
data Result error x
    = Success x
    | Failure error

f :: Result error x -> Text
f (Success v_x)      = "SUCCESS" -- v_x
f (Failure v_error)  = "FAILURE" -- v_error

f' :: Result error x -> Text
f' result = case result of
    Success v_x     -> "SUCCESS" -- v_x
    Failure v_error -> "FAILURE" -- v_error
```

# **Result error x** in Java

The **Result** type can be used to indicate that a function may fail to produce a value.

```
data Result error x
    = Success x
    | Failure error

f :: Result error x -> Text
f (Success v_x)      = "SUCCESS" -- v_x
f (Failure v_error)  = "FAILURE" -- v_error
```

# **Result error x** in Java

The **Result** type can be used to indicate that a function may fail to produce a value.

```
data Result error x
    = Success x
    | Failure error

f :: Result error x -> Text
f (Success v_x)      = "SUCCESS" -- v_x
f (Failure v_error)  = "FAILURE" -- v_error

String f(final Result<X> result) {
    return result.match(
        success     -> "SUCCESS", // success.value
        failure     -> "FAILURE"  // failure.exception
    );
}
```

# **Result error x** in Java

The **Result** type can be used to indicate that a function may fail to produce a value.

```
data Result error x
    = Success x
    | Failure error

f :: Result error x -> Text
f (Success v_x)      = "SUCCESS" -- v_x
f (Failure v_error)  = "FAILURE" -- v_error

String f(final Result<X> result) {
    return result.match(
        success     -> "SUCCESS", // success.value
        failure     -> "FAILURE"  // failure.exception
    );
}

public abstract class Result<X> {
    ... elided ...
    @FunctionalInterface
    public interface PatternMatchSuccess<X, R> { R match(Success<X> success); }

    @FunctionalInterface
    public interface PatternMatchFailure<X, R> { R match(Failure<X> failure); }
}
```

# **Result error x** in Java

The **Result** type can be used to indicate that a function may fail to produce a value.

```
String f(final Result<X> result) {
    return result.match(
        success     -> "SUCCESS", // success.value
        failure     -> "FAILURE"  // failure.exception
    );
}

public abstract class Result<X> {
    ... elided ...
    public static final class Success<X> extends Result<X> {
        ... elided ...
        public <R> R match(final PatternMatchSuccess<X, R> success, final PatternMatchFailure<X, R> failure) {
            return success.match(this);
        }
    }
    public static final class Failure<X> extends Result<X> {
        ... elided ...
        public <R> R match(final PatternMatchSuccess<X, R> success, final PatternMatchFailure<X, R> failure) {
            return failure.match(this);
        }
    }
    ... elided ...
}
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

```
instance Functor Maybe where
    fmap :: (x -> r) -> Maybe x -> Maybe r
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

```
instance Functor Maybe where
    fmap :: (x -> r) -> Maybe x -> Maybe r
    fmap f_x_r (Just v_x)           = Just (f_x_r v_r)
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

```
instance Functor Maybe where
    fmap :: (x -> r) -> Maybe x -> Maybe r
    fmap f_x_r (Just v_x)           = Just (f_x_r v_r)
    fmap f_x_r Nothing              = Nothing
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

```
instance Functor Maybe where
    fmap :: (x -> r) -> Maybe x -> Maybe r
    fmap f_x_r (Just v_x)           = Just (f_x_r v_r)
    fmap f_x_r Nothing              = Nothing

instance Functor (Result error) where
    fmap :: (x -> r) -> Result error x -> Result error r
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

```
instance Functor Maybe where
    fmap :: (x -> r) -> Maybe x -> Maybe r
    fmap f_x_r (Just v_x)           = Just (f_x_r v_r)
    fmap f_x_r Nothing              = Nothing

instance Functor (Result error) where
    fmap :: (x -> r) -> Result error x -> Result error r
    fmap f_x_r (Success v_x)        = Success (f_x_r v_x)
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

```
instance Functor Maybe where
    fmap :: (x -> r) -> Maybe x -> Maybe r
    fmap f_x_r (Just v_x)           = Just (f_x_r v_r)
    fmap f_x_r Nothing              = Nothing

instance Functor (Result error) where
    fmap :: (x -> r) -> Result error x -> Result error r
    fmap f_x_r (Success v_x)        = Success (f_x_r v_x)
    fmap f_x_r (Failure v_error)    = Failure v_error
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

```
instance Functor Maybe where
    fmap :: (x -> r) -> Maybe x -> Maybe r
    fmap f_x_r (Just v_x)           = Just (f_x_r v_r)
    fmap f_x_r Nothing              = Nothing

instance Functor (Result error) where
    fmap :: (x -> r) -> Result error x -> Result error r
    fmap f_x_r (Success v_x)        = Success (f_x_r v_x)
    fmap f_x_r (Failure v_error)    = Failure v_error

instance Functor List where
    fmap :: (x -> r) -> List x -> List r
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

```
instance Functor Maybe where
    fmap :: (x -> r) -> Maybe x -> Maybe r
    fmap f_x_r (Just v_x)           = Just (f_x_r v_r)
    fmap f_x_r Nothing              = Nothing

instance Functor (Result error) where
    fmap :: (x -> r) -> Result error x -> Result error r
    fmap f_x_r (Success v_x)        = Success (f_x_r v_x)
    fmap f_x_r (Failure v_error)    = Failure v_error

instance Functor List where
    fmap :: (x -> r) -> List x -> List r
    fmap f_x_r (Element v_x v_rest) = Element (f_x_r v_x) (fmap f_x_r v_rest)
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

```
instance Functor Maybe where
    fmap :: (x -> r) -> Maybe x -> Maybe r
    fmap f_x_r (Just v_x)           = Just (f_x_r v_r)
    fmap f_x_r Nothing              = Nothing

instance Functor (Result error) where
    fmap :: (x -> r) -> Result error x -> Result error r
    fmap f_x_r (Success v_x)        = Success (f_x_r v_x)
    fmap f_x_r (Failure v_error)    = Failure v_error

instance Functor List where
    fmap :: (x -> r) -> List x -> List r
    fmap f_x_r (Element v_x v_rest) = Element (f_x_r v_x) (fmap f_x_r v_rest)
    fmap f_x_r Empty                = Empty
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

fmap identity functor          ==   identity functor
fmap (f_y_r . f_x_y) functor   ==   (fmap f_y_r . fmap f_x_y) functor
```

```
instance Functor Maybe where
    fmap :: (x -> r) -> Maybe x -> Maybe r
    fmap f_x_r (Just v_x)           = Just (f_x_r v_r)
    fmap f_x_r Nothing              = Nothing

instance Functor (Result error) where
    fmap :: (x -> r) -> Result error x -> Result error r
    fmap f_x_r (Success v_x)        = Success (f_x_r v_x)
    fmap f_x_r (Failure v_error)    = Failure v_error

instance Functor List where
    fmap :: (x -> r) -> List x -> List r
    fmap f_x_r (Element v_x v_rest) = Element (f_x_r v_x) (fmap f_x_r v_rest)
    fmap f_x_r Empty                = Empty
```

**Note that the _structure_ of the mapped values never changes.**

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

public abstract <R> Result<R> fmap(Function<X, R> function);
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

public abstract <R> Result<R> fmap(Function<X, R> function);

public static final class Success<X> extends Result<X> {
    public final X value;
    ... elided ...
    public <R> Result<R> fmap(final Function<X, R> function) {
        Objects.requireNonNull(function, "Missing 'function'.");
        return new Success(function.apply(this.value));
    }
    ... elided ...
}
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

public abstract <R> Result<R> fmap(Function<X, R> function);

public static final class Success<X> extends Result<X> {
    public final X value;
    ... elided ...
    public <R> Result<R> fmap(final Function<X, R> function) {
        Objects.requireNonNull(function, "Missing 'function'.");
        return new Success(function.apply(this.value));
    }
    ... elided ...
}

public static final class Failure<X> extends Result<X> {
    public final Exception exception;
    ... elided ...
    public <R> Result<R> fmap(final Function<X, R> function) {
        Objects.requireNonNull(function, "Missing 'function'.");
        return (Failure<R>) this;
    }
    ... elided ...
}
```

# Functor or Mappable

A **Functor** is a type that can be mapped over.

```
class Functor functor where
    fmap :: (x -> r) -> functor x -> functor r

public abstract <R> Result<R> fmap(Function<X, R> function);

public static final class Success<X> extends Result<X> {
    public final X value;
    ... elided ...
    public <R> Result<R> fmap(final Function<X, R> function) {
        Objects.requireNonNull(function, "Missing 'function'.");
        return new Success(function.apply(this.value));
    }
    ... elided ...
}

public static final class Failure<X> extends Result<X> {
    public final Exception exception;
    ... elided ...
    public <R> Result<R> fmap(final Function<X, R> function) {
        Objects.requireNonNull(function, "Missing 'function'.");
        return (Failure<R>) this;
    }
    ... elided ...
}
```

**Note that the _structure_ of the mapped values never changes.**

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

g :: (x -> y -> z -> r) -> Maybe x -> Maybe y -> Maybe z -> Maybe r
g f maybe_x maybe_y maybe_z
    = f `fmap` maybe_x `apply` maybe_y `apply` maybe_z
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

g :: (x -> y -> z -> r) -> Maybe x -> Maybe y -> Maybe z -> Maybe r
g f maybe_x maybe_y maybe_z
    = maybe_y_z_r      `apply` maybe_y `apply` maybe_z
        where

            maybe_y_z_r = f `fmap` maybe_x
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

g :: (x -> y -> z -> r) -> Maybe x -> Maybe y -> Maybe z -> Maybe r
g f maybe_x maybe_y maybe_z
    = maybe_y_z_r      `apply` maybe_y `apply` maybe_z
        where
            maybe_y_z_r :: Maybe (y -> z -> r)
            maybe_y_z_r = f `fmap` maybe_x
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

g :: (x -> y -> z -> r) -> Maybe x -> Maybe y -> Maybe z -> Maybe r
g f maybe_x maybe_y maybe_z
    = maybe_z_r                        `apply` maybe_z
        where
            maybe_y_z_r :: Maybe (y -> z -> r)
            maybe_y_z_r = f `fmap` maybe_x

            maybe_z_r = maybe_y_z_r `apply` maybe_y
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

g :: (x -> y -> z -> r) -> Maybe x -> Maybe y -> Maybe z -> Maybe r
g f maybe_x maybe_y maybe_z
    = maybe_z_r                        `apply` maybe_z
        where
            maybe_y_z_r :: Maybe (y -> z -> r)
            maybe_y_z_r = f `fmap` maybe_x
            maybe_z_r :: Maybe (z -> r)
            maybe_z_r = maybe_y_z_r `apply` maybe_y
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

g :: (x -> y -> z -> r) -> Maybe x -> Maybe y -> Maybe z -> Maybe r
g f maybe_x maybe_y maybe_z
    = maybe_r
        where
            maybe_y_z_r :: Maybe (y -> z -> r)
            maybe_y_z_r = f `fmap` maybe_x
            maybe_z_r :: Maybe (z -> r)
            maybe_z_r = maybe_y_z_r `apply` maybe_y

            maybe_r = maybe_z_r `apply` maybe_z
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

g :: (x -> y -> z -> r) -> Maybe x -> Maybe y -> Maybe z -> Maybe r
g f maybe_x maybe_y maybe_z
    = maybe_r
        where
            maybe_y_z_r :: Maybe (y -> z -> r)
            maybe_y_z_r = f `fmap` maybe_x
            maybe_z_r :: Maybe (z -> r)
            maybe_z_r = maybe_y_z_r `apply` maybe_y
            maybe_r :: Maybe r
            maybe_r = maybe_z_r `apply` maybe_z
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

instance Applicative Maybe where
    apply :: Maybe (x -> r) -> Maybe x -> Maybe r
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

instance Applicative Maybe where
    apply :: Maybe (x -> r) -> Maybe x -> Maybe r
    apply :: (Just f_x_r) (Just x) = Just (f_x_r x)
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

instance Applicative Maybe where
    apply :: Maybe (x -> r) -> Maybe x -> Maybe r
    apply :: (Just f_x_r) (Just x) = Just (f_x_r x)
    apply :: _            _        = Nothing
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

instance Applicative Maybe where
    apply :: Maybe (x -> r) -> Maybe x -> Maybe r
    apply :: (Just f_x_r) (Just x) = Just (f_x_r x)
    apply :: _            _        = Nothing

instance Applicative (Result error) where
    apply :: Result error (x -> r) -> Result error x -> Result error r
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

instance Applicative Maybe where
    apply :: Maybe (x -> r) -> Maybe x -> Maybe r
    apply :: (Just f_x_r) (Just x) = Just (f_x_r x)
    apply :: _            _        = Nothing

instance Applicative (Result error) where
    apply :: Result error (x -> r) -> Result error x -> Result error r
    apply :: (Success f_x_r)   (Success x)       = Success (f_x_r x)
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

instance Applicative Maybe where
    apply :: Maybe (x -> r) -> Maybe x -> Maybe r
    apply :: (Just f_x_r) (Just x) = Just (f_x_r x)
    apply :: _            _        = Nothing

instance Applicative (Result error) where
    apply :: Result error (x -> r) -> Result error x -> Result error r
    apply :: (Success f_x_r)   (Success x)       = Success (f_x_r x)
    apply :: (Failure v_error) _                 = Failure v_error
    apply :: _                 (Failure v_error) = Failure v_error
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

instance Applicative Maybe where
    apply :: Maybe (x -> r) -> Maybe x -> Maybe r
    apply :: (Just f_x_r) (Just x) = Just (f_x_r x)
    apply :: _            _        = Nothing

instance Applicative (Result error) where
    apply :: Result error (x -> r) -> Result error x -> Result error r
    apply :: (Success f_x_r)   (Success x)       = Success (f_x_r x)
    apply :: (Failure v_error) _                 = Failure v_error
    apply :: _                 (Failure v_error) = Failure v_error

instance Applicative List where
    apply :: List (x -> r) -> List x -> List r
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

instance Applicative Maybe where
    apply :: Maybe (x -> r) -> Maybe x -> Maybe r
    apply :: (Just f_x_r) (Just x) = Just (f_x_r x)
    apply :: _            _        = Nothing

instance Applicative (Result error) where
    apply :: Result error (x -> r) -> Result error x -> Result error r
    apply :: (Success f_x_r)   (Success x)       = Success (f_x_r x)
    apply :: (Failure v_error) _                 = Failure v_error
    apply :: _                 (Failure v_error) = Failure v_error

instance Applicative List where
    apply :: List (x -> r) -> List x -> List r
    apply :: (Element f_x_r lft_rest) (Element x rgt_rest) = Element (f_x_r x) (lft_rest `apply` rgt_rest)
```

# Applicative (Functor)

An **Applicative** is a type that can sequence computations.

```
class Functor applicative => Applicative applicative where
    apply :: applicative (x -> r) -> applicative x -> applicative r

instance Applicative Maybe where
    apply :: Maybe (x -> r) -> Maybe x -> Maybe r
    apply :: (Just f_x_r) (Just x) = Just (f_x_r x)
    apply :: _            _        = Nothing

instance Applicative (Result error) where
    apply :: Result error (x -> r) -> Result error x -> Result error r
    apply :: (Success f_x_r)   (Success x)       = Success (f_x_r x)
    apply :: (Failure v_error) _                 = Failure v_error
    apply :: _                 (Failure v_error) = Failure v_error

instance Applicative List where
    apply :: List (x -> r) -> List x -> List r
    apply :: (Element f_x_r lft_rest) (Element x rgt_rest) = Element (f_x_r x) (lft_rest `apply` rgt_rest)
    apply :: _                        _                    = Empty
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

# Monad

A **Monad** is a type that represents a _composable_ computation.

A **Monad** is the minimal amount of structure needed to overload function composition in a way that
"performs an extra computation" on the intermediate value.

# Monad

A **Monad** is a type that represents a _composable_ computation.

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                Success address   ->
                    case getCity database address of
                        Success city   -> Success (showCity city)
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                Success address   ->
                    case getCity database address of
                        Success city   -> Success (showCity city)
                        Failure noCity -> Failure noCity
                Failure noAddress -> Failure noAddress
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
instance Monad Maybe where
    bind :: Maybe x -> (x -> Maybe r) -> Maybe r
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
instance Monad Maybe where
    bind :: Maybe x -> (x -> Maybe r) -> Maybe r
    bind (Just v_x) f_x_maybe_r = f_x_maybe_r v_x
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
instance Monad Maybe where
    bind :: Maybe x -> (x -> Maybe r) -> Maybe r
    bind (Just v_x) f_x_maybe_r = f_x_maybe_r v_x
    bind Nothing    _           = Nothing
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
instance Monad Maybe where
    bind :: Maybe x -> (x -> Maybe r) -> Maybe r
    bind (Just v_x) f_x_maybe_r = f_x_maybe_r v_x
    bind Nothing    _           = Nothing

instance Monad (Result error) where
    bind :: Result error x -> (x -> Result error r) -> Result error r
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
instance Monad Maybe where
    bind :: Maybe x -> (x -> Maybe r) -> Maybe r
    bind (Just v_x) f_x_maybe_r = f_x_maybe_r v_x
    bind Nothing    _           = Nothing

instance Monad (Result error) where
    bind :: Result error x -> (x -> Result error r) -> Result error r
    bind (Success v_x)     f_x_result_error_r = f_x_result_error_r v_x
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
instance Monad Maybe where
    bind :: Maybe x -> (x -> Maybe r) -> Maybe r
    bind (Just v_x) f_x_maybe_r = f_x_maybe_r v_x
    bind Nothing    _           = Nothing

instance Monad (Result error) where
    bind :: Result error x -> (x -> Result error r) -> Result error r
    bind (Success v_x)     f_x_result_error_r = f_x_result_error_r v_x
    bind (Failure v_error) _                  = Failure v_error
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
instance Monad Maybe where
    bind :: Maybe x -> (x -> Maybe r) -> Maybe r
    bind (Just v_x) f_x_maybe_r = f_x_maybe_r v_x
    bind Nothing    _           = Nothing

instance Monad (Result error) where
    bind :: Result error x -> (x -> Result error r) -> Result error r
    bind (Success v_x)     f_x_result_error_r = f_x_result_error_r v_x
    bind (Failure v_error) _                  = Failure v_error

instance Monad List where
    bind :: List x -> (x -> List r) -> List r
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
instance Monad Maybe where
    bind :: Maybe x -> (x -> Maybe r) -> Maybe r
    bind (Just v_x) f_x_maybe_r = f_x_maybe_r v_x
    bind Nothing    _           = Nothing

instance Monad (Result error) where
    bind :: Result error x -> (x -> Result error r) -> Result error r
    bind (Success v_x)     f_x_result_error_r = f_x_result_error_r v_x
    bind (Failure v_error) _                  = Failure v_error

instance Monad List where
    bind :: List x -> (x -> List r) -> List r
    bind (Element v_x v_rest) f_x_list_r = (f_x_list_r v_x) ++ (v_rest `bind` f_x_list_r)

        where
            (++) :: List x -> List x -> List x
            (++) = ...
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
instance Monad Maybe where
    bind :: Maybe x -> (x -> Maybe r) -> Maybe r
    bind (Just v_x) f_x_maybe_r = f_x_maybe_r v_x
    bind Nothing    _           = Nothing

instance Monad (Result error) where
    bind :: Result error x -> (x -> Result error r) -> Result error r
    bind (Success v_x)     f_x_result_error_r = f_x_result_error_r v_x
    bind (Failure v_error) _                  = Failure v_error

instance Monad List where
    bind :: List x -> (x -> List r) -> List r
    bind (Element v_x v_rest) f_x_list_r = (f_x_list_r v_x) ++ (v_rest `bind` f_x_list_r)
    bind Empty                _          = Empty
        where
            (++) :: List x -> List x -> List x
            (++) = ...
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                Success address   ->
                    case getCity database address of
                        Success city   -> Success (showCity city)
                        Failure noCity -> Failure noCity
                Failure noAddress -> Failure noAddress
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                Success address   ->
                    case getCity database address of
                        Success city   -> Success (showCity city)
                        Failure noCity -> Failure noCity
                Failure noAddress -> Failure noAddress
        Failure noPerson -> Failure noPerson

showCity' :: Result Text City -> Result Text Text
showCity' cityResult = fmap showCity cityResult
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                Success address   ->
                    case getCity database address of
                        Success city   -> Success (showCity city)
                        Failure noCity -> Failure noCity
                Failure noAddress -> Failure noAddress
        Failure noPerson -> Failure noPerson

showCity' :: Result Text City -> Result Text Text
showCity' = fmap showCity
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                Success address   ->
                    case getCity database address of
                        city -> showCity `fmap` city

                Failure noAddress -> Failure noAddress
        Failure noPerson -> Failure noPerson

showCity' :: Result Text City -> Result Text Text
showCity' = fmap showCity
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                Success address   ->
                    case getCity database address of
                        city -> showCity `fmap` city
                Failure noAddress -> Failure noAddress
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                Success address   ->

                                showCity `fmap` getCity database address
                Failure noAddress -> Failure noAddress
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                Success address   ->
                    showCity `fmap` getCity database address
                Failure noAddress -> Failure noAddress
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                Success address   ->
                           showCity `fmap`                getCity database address
                Failure noAddress -> Failure noAddress
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of

                address -> showCity `fmap` address `bind` getCity database

        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                address -> showCity `fmap` address `bind` getCity database
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            case getAddress database person of
                address -> showCity `fmap` address                    `bind` getCity database
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->

                           showCity `fmap` getAddress database person `bind` getCity database
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
            showCity `fmap` getAddress database person `bind` getCity database
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        Success person   ->
                  showCity `fmap`               getAddress database person `bind` getCity database
        Failure noPerson -> Failure noPerson
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of

        person -> showCity `fmap` person `bind` getAddress database        `bind` getCity database

```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        person -> showCity `fmap` person `bind` getAddress database `bind` getCity database
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    case getPerson database personId of
        person -> showCity `fmap` person                      `bind` getAddress database `bind` getCity database
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =

                  showCity `fmap` getPerson database personId `bind` getAddress database `bind` getCity database
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

```
getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` getPerson database personId `bind` getAddress database `bind` getCity database
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final class Success<X> extends Result<X> {
    public final X value;
    ... elided ...
    public <R> Result<R> bind(final Function<X, Result<R>> function) {
        Objects.requireNonNull(function, "Missing 'function'.");
        final Result<R> result = function.apply(this.value);
        Objects.requireNonNull(result, "Missing 'result'.");
        return result;
    }
    ... elided ...
}
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final class Success<X> extends Result<X> {
    public final X value;
    ... elided ...
    public <R> Result<R> bind(final Function<X, Result<R>> function) {
        Objects.requireNonNull(function, "Missing 'function'.");
        final Result<R> result = function.apply(this.value);
        Objects.requireNonNull(result, "Missing 'result'.");
        return result;
    }
    ... elided ...
}

public static final class Failure<X> extends Result<X> {
    public final Exception exception;
    ... elided ...
    public <R> Result<R> bind(final Function<X, Result<R>> function) {
        Objects.requireNonNull(function, "Missing 'function'.");
        return (Result<R>) this;
    }
    ... elided ...
}
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

getPerson  :: Database -> PersonId -> Result Text Person
getAddress :: Database -> Person   -> Result Text Address
getCity    :: Database -> Address  -> Result Text City

showCity :: City -> Text

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final Result<Person>  getPerson (final Database database, final PersonId personId) { ... }
public static final Result<Address> getAddress(final Database database, final Person   person)   { ... }
public static final Result<City>    getCity   (final Database database, final Address  address)  { ... }

public static final String showCity(final City city) { ... }

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final Result<Person>  getPerson (final Database database, final PersonId personId) { ... }
public static final Result<Address> getAddress(final Database database, final Person   person)   { ... }
public static final Result<City>    getCity   (final Database database, final Address  address)  { ... }

public static final String showCity(final City city) { ... }

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)

public static final Result<String> getCityAsText(final Database database, final PersonId personId) {
    return getPerson(database, personId)
            .bind(person -> getAddress(database, person))
            .bind(address -> getCity(database, address))
            .fmap(city -> showCity(city));
}
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final Result<Person>  getPerson (final Database database, final PersonId personId) { ... }
public static final Result<Address> getAddress(final Database database, final Person   person)   { ... }
public static final Result<City>    getCity   (final Database database, final Address  address)  { ... }

public static final String showCity(final City city) { ... }

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)

public static final Result<String> getCityAsText(final Database database, final PersonId personId) {
    return SomeClass.getPerson(database, personId)
            .bind(person -> SomeClass.getAddress(database, person))
            .bind(address -> SomeClass.getCity(database, address))
            .fmap(city -> SomeClass.showCity(city));
}
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final Result<Person>  getPerson (final Database database, final PersonId personId) { ... }
public static final Result<Address> getAddress(final Database database, final Person   person)   { ... }
public static final Result<City>    getCity   (final Database database, final Address  address)  { ... }

public static final String showCity(final City city) { ... }

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)

public static final Result<String> getCityAsText(final Database database, final PersonId personId) {
    return SomeClass.getPerson(database, personId)
            .bind(person -> SomeClass.getAddress(database, person))
            .bind(address -> SomeClass.getCity(database, address))
            .fmap(city -> SomeClass.showCity(city));
}

public static final <X, Y, R> Function1<Y, R> curry2(final Function2<X, Y, R> function, final X v_x) {
    Objects.requireNonNull(function, "Missing 'function'.");
    return v_y -> function.apply(v_x, v_y);
}
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final Result<Person>  getPerson (final Database database, final PersonId personId) { ... }
public static final Result<Address> getAddress(final Database database, final Person   person)   { ... }
public static final Result<City>    getCity   (final Database database, final Address  address)  { ... }

public static final String showCity(final City city) { ... }

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)

public static final Result<String> getCityAsText(final Database database, final PersonId personId) {
    return SomeClass.getPerson(database, personId)
            .bind(person -> curry2(SomeClass::getAddress, database).apply(person))
            .bind(address -> SomeClass.getCity(database, address))
            .fmap(city -> SomeClass.showCity(city));
}

public static final <X, Y, R> Function1<Y, R> curry2(final Function2<X, Y, R> function, final X v_x) {
    Objects.requireNonNull(function, "Missing 'function'.");
    return v_y -> function.apply(v_x, v_y);
}
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final Result<Person>  getPerson (final Database database, final PersonId personId) { ... }
public static final Result<Address> getAddress(final Database database, final Person   person)   { ... }
public static final Result<City>    getCity   (final Database database, final Address  address)  { ... }

public static final String showCity(final City city) { ... }

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)

public static final Result<String> getCityAsText(final Database database, final PersonId personId) {
    return SomeClass.getPerson(database, personId)
            .bind(curry2(SomeClass::getAddress, database))
            .bind(address -> SomeClass.getCity(database, address))
            .fmap(city -> SomeClass.showCity(city));
}

public static final <X, Y, R> Function1<Y, R> curry2(final Function2<X, Y, R> function, final X v_x) {
    Objects.requireNonNull(function, "Missing 'function'.");
    return v_y -> function.apply(v_x, v_y);
}
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final Result<Person>  getPerson (final Database database, final PersonId personId) { ... }
public static final Result<Address> getAddress(final Database database, final Person   person)   { ... }
public static final Result<City>    getCity   (final Database database, final Address  address)  { ... }

public static final String showCity(final City city) { ... }

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)

public static final Result<String> getCityAsText(final Database database, final PersonId personId) {
    return SomeClass.getPerson(database, personId)
            .bind(curry2(SomeClass::getAddress, database))
            .bind(address -> curry2(SomeClass::getCity, database).apply(address))
            .fmap(city -> SomeClass.showCity(city));
}

public static final <X, Y, R> Function1<Y, R> curry2(final Function2<X, Y, R> function, final X v_x) {
    Objects.requireNonNull(function, "Missing 'function'.");
    return v_y -> function.apply(v_x, v_y);
}
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final Result<Person>  getPerson (final Database database, final PersonId personId) { ... }
public static final Result<Address> getAddress(final Database database, final Person   person)   { ... }
public static final Result<City>    getCity   (final Database database, final Address  address)  { ... }

public static final String showCity(final City city) { ... }

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)

public static final Result<String> getCityAsText(final Database database, final PersonId personId) {
    return SomeClass.getPerson(database, personId)
            .bind(curry2(SomeClass::getAddress, database))
            .bind(curry2(SomeClass::getCity, database))
            .fmap(city -> SomeClass.showCity(city));
}

public static final <X, Y, R> Function1<Y, R> curry2(final Function2<X, Y, R> function, final X v_x) {
    Objects.requireNonNull(function, "Missing 'function'.");
    return v_y -> function.apply(v_x, v_y);
}
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final Result<Person>  getPerson (final Database database, final PersonId personId) { ... }
public static final Result<Address> getAddress(final Database database, final Person   person)   { ... }
public static final Result<City>    getCity   (final Database database, final Address  address)  { ... }

public static final String showCity(final City city) { ... }

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)

public static final Result<String> getCityAsText(final Database database, final PersonId personId) {
    return SomeClass.getPerson(database, personId)
            .bind(curry2(SomeClass::getAddress, database))
            .bind(curry2(SomeClass::getCity, database))
            .fmap(SomeClass::showCity);
}

public static final <X, Y, R> Function1<Y, R> curry2(final Function2<X, Y, R> function, final X v_x) {
    Objects.requireNonNull(function, "Missing 'function'.");
    return v_y -> function.apply(v_x, v_y);
}
```

# Monad

A **Monad** is a type that represents a _composable_ computation.

```
class Applicative monad => Monad monad where
    bind :: monad x -> (x -> monad r) -> monad r

public abstract <R> Result<R> bind(Function<X, Result<R>> function);

public static final Result<Person>  getPerson (final Database database, final PersonId personId) { ... }
public static final Result<Address> getAddress(final Database database, final Person   person)   { ... }
public static final Result<City>    getCity   (final Database database, final Address  address)  { ... }

public static final String showCity(final City city) { ... }

getCityAsText :: Database -> PersonId -> Result Text Text
getCityAsText database personId =
    showCity `fmap` (getPerson database personId `bind` getAddress database `bind` getCity database)

public static final Result<String> getCityAsText(final Database database, final PersonId personId) {
    return SomeClass.getPerson(database, personId)
            .bind(curry2(SomeClass::getAddress, database))
            .bind(curry2(SomeClass::getCity, database))
            .fmap(SomeClass::showCity);
}

public static final <X, Y, R> Function1<Y, R> curry2(final Function2<X, Y, R> function, final X v_x) {
    Objects.requireNonNull(function, "Missing 'function'.");
    return v_y -> function.apply(v_x, v_y);
}
```
