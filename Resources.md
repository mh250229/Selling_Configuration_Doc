# Resources

## General

Selling Configuration is an extensive set of configuration supporting fine grained tuning of the Selling Cart Service.

Not all configurations are mandatory even for a full production environment of a given tenant.

Many resources may be left blank to get a reasonable default behavior.

**Important:**

Selling Application clients are not expected to read all Selling Configuration and "act" on them. Instead, such clients should use the Selling Cart Service that will act according to the Selling Configuration.

In the few cases where Selling Application clients would need to read Selling Configurations (for example get available tender types), it is in order to obtain their resource Id.

Selling configuration exposes a set of "/effective" endpoints for obtaining relevant configuration for a given Store and Touch-Point Group.

Many configurations allow definitions per Enterprise Unit and Touch-Point Group.

Configuration takes effect according to the "nearest" Enterprise Unit in the Hierarchy.

For example, if a Configuration is defined to Root, it applies to all Stores.

If the same type of Configuration is defined at a Store or Region level it will override the configuration on the Root.
If a Configuration is defined for a Specific Touch-Point Group, it would apply only to that Group.

## Additional resources

Selling Configuration exposes many additional configurations covering all aspects of the Cart operation.

These resources follow the same principles as the above main resources and can be seen in the Selling Configuration API spec.
