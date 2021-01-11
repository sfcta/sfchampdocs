---------------------
Network Supply Models
---------------------
The supply models consist of assigning travel demand onto transportation networks, and then evaluating how those transportation networks perform. There are separate models for roadway and transit supply. Both models use the Citilabs Cube software package for assignment (assigning trips to networks) and skimming (evaluating travel times and costs for travel between origins and destinations after trips have been assigned to the networks).

Highway Models
^^^^^^^^^^^^^^
Highway assignment is the process of loading vehicle trips onto the roadway network. In assignment, each vehicle trip searches for a route with the lowest generalized cost (considering travel time and toll costs). The assignment model iteratively reassigns trips until the model converges towards a user-equilibrium condition. Skimming is the process of evaluating the components of generalized cost for all origin and destination pairs. Assignment and skimming is conducted separately for the five SF-CHAMP time of day periods: AM Peak, midday, PM Peak, evening, and late night/early morning.

Highway Assignment
~~~~~~~~~~~~~~~~~~

Highway Skimming
~~~~~~~~~~~~~~~~

Transit Models
^^^^^^^^^^^^^^
Transit assignment and skimming is similar to highway assignment and skimming, except that transit trips are assigned to the transit network. Transit assignment is inherently more complicated because transit trips can include walk or drive access segments, one or more transit services, and transit trips face a variety of fare policies. SF-CHAMP uses Citilabs Cube software for transit assignment and skimming.

Transit Assignment
~~~~~~~~~~~~~~~~~~

Transit Skimming
~~~~~~~~~~~~~~~~

Walk Models
^^^^^^^^^^^

Bike Models
^^^^^^^^^^^
