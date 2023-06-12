## Anemic Types

Anemic types are types without any behavior and implicit validation

For example: Person model with just plain properties

## Rich Types

Rich types are types with behavior and usually implicit validation.

## Entities 

- They are types with an identity. 
    - identity is an additional property that defines and distinguish them.
- They can exist on its own. 
- They are mutable 
- We should not add any behavior to the entity
- They can be in a invalid state, so we should remember about validation

For example: Person, Organization

## Value Objects

The most important characteristics of value types:
- They are explicit domain concepts
- They are always in a valid state
- They are immutable
- They are defined by a value (no identity, like a color)

Other characteristics:
- We can add behavior to value objects (like to Rich Types)
- The lifespan of a value type instance is bounded by the lifespan of the owning entity instance.

For instance **Address* can be a value object. 
If an address changes, we should change the whole address, not only the city.
The address do not need identity, it is defined by the real place in the world.

