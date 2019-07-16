# instance-resolver

## Usage

```php
use InstanceResolver\ResolverClass;
class A
{
    public $prop = 0;
}
class B extends A
{
    public $prop = 0;
}
class C
{
    public function __construct(A $a){}
}
class D
{
    public function __construct($x){}
}
$resolver = new ResolverClass($container);
$a = $resolver(A::class);
$b = $resolver(B::class);
$c = $resolver(C::class);
$d = $resolver(D::class); // throw new InstanceResolver\Exception\UnresolvedParameter
                          // --> le paramètre $x ne peut pas être résolu
$e = $resolver('E'); // throw new InstanceResolver\Exception\UnresolvedClass
                     // --> la classe E n'existe pas et n'a pas été trouvé par l'autoloader
```

Pour déclarer les dépendance dans le Container, il faut utiliser les nom de classe complet.

## TODO

### version 1.0

- [X] résoudre le problème de namespace
- [X] coriger tout les tests
- [X] faire l'ébauche de la doc
- [X] publier la version 1.0