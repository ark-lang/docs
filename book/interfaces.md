# Interfaces
![Feature Planned](Badge_Planned.svg)

Interfaces are named collections of method signatures. In Ark, interfaces are implicit, which means that if something has the methods defined in an interface `A`, it will implicitly implement interface `A`.

This follows the philosophy of duck typing:

> If it looks like a duck, and quacks like a duck, it's a duck"

In other words, if you have an interface `A`, and a structure `B` where `B` contains all of the properties defined in interface `A`, that structure is `A`.

```
type Geometry interface {
    area() -> f64;
    perimeter() -> f64;
};
```

Now if we introduce some structures that implement the same methods in the interface we defined, they will implement `Geometry` implicitly.

```
type Rectangle struct {
    width: f64,
    height: f64,
};

type Circle struct {
    radius: f64,
};

func (r: ^Rectangle) area() -> f64 {
    return r.width * r.height;
}

func (r: ^Rectangle) perimeter() -> f64 {
    return (r.width * 2) * (r.height * 2);
}

func (c: ^Circle) area() -> f64 {
    return PI * c.radius * c.radius;
}

func (c: ^Circle) perimeter() -> f64 {
    return 2 * PI * c.radius;
}
```

We can make a generic function that takes any type that implements our Geometry interface:

```
func calculate(g: Geometry) {
    C::printf(c"area %f, perim %f \n", g.area(), g.perimeter());
}

func main() -> int {
    r := Rect { 
        width: 3, 
        height: 4,
    };
    
    c := Circle {
        radius: 5,
    };

    calculate(r);
    calculate(c);
}
```