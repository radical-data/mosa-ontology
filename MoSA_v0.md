 Museum of Stolen Artifacts v0 table { font-family: arial, sans-serif; border-collapse: collapse; width: 100%; } td, th { border: 1px solid #dddddd; text-align: left; padding: 8px; } tr:nth-child(odd) { background-color: #dddddd; }

Museum of Stolen Artifacts Ontology v0
======================================

* * *

_For questions or criticisms, please contact Valentin (at <valevogelmann _at_\> gmail _dot_ com), who maintains this document._

This is the first, basic version of the _Museum of Stolen Artifacts Ontology_ (_MoSA_ for short) and not even a draft, thus subject to constant changes. This is the document which can be referred to when structuring data using the MoSA ontology — all of the entities and predicates the MoSA ontology defines are listed below including their domains, ranges and relationships.

* * *

Entities
--------

Since we are taking an iterative and bottom-up approach, this ontology is not defined with as a hierarchy of entities with a top-level element. It means that we only define the entities we "need" for making data more useful and clarifying intentions. For instance, it also means that (for now) we don't make commitments about _what_ the objects in the Museum of Stolen Artifacts are.

### Layer Entities

We do want to distinguish the different "layers of existence" of that might (or might not) apply to an object, for now these are (1) of course its physical manifestation(s) and (2) digital records that witness their existence and describe them. The latter are, however, typically taken from institutions in those countries that have stolen them, and this is a core reason for making this distinction explicit: Separating objects from what different parties say about them, can allow us to question and contest.

PhysicalManifestation

*   Definition:
*   Usage notes:

DigitalRecord

*   Definition: A record in a digital collection, dataset, etc which witnesses or claims the existence of an object (physical or not) and describes typically aspects of it.
*   Usage notes: This entity type mainly serves the purpose of bringing together information from various institutional collection systems but can explicitly also be used to create new records. Note, however, that of course an entry in the MoSA itself is also a _DigitalRecord_ but we reserve this entity for representing _external_ digital records.
*   Required properties:
    *   [identified\_by](#identified_by): Making it possible to refer back to the record in its original context; requiring an identifier _should_ be possible because of the digital nature of this entity.
    *   [assigned\_title](#assigned_title): For human identification of records, it is covenient to have a title; could be forged in case not present in an original record.

### Object-Context Entities

Museum

*   Superclasses: \[UNDER CONSTRUCTION: it might be useful to create a fuller ontology (i.e. hierarchy) of institutional and non-institutional entities that are actors in the context of stolen artefacts. the superclass of a **(Western)** _Museum_ could then be something like "(Western) Institution"?
*   Subclasses: \[UNDER CONSTRUCTION: It could become useful to distinguish different kinds of _(Western)_ museums?\]
*   Definition: \[UNDER CONSTRUCTION: A (public) institution which holds an object in the MoSA, i.e. a stolen artefact, and is the provider of the information in a [DigitalRecord](#DigitalRecord).\]
*   Usage notes: \[UNDER CONSTRUCTION: This entity class has been created on the fly out of the need to "name" entities like the British Museum, Wereldmuseum and Musei Vaticani. The name of this class as well as its meaning are very much open for debate.\]

### Provenance Entities

ProvGeneric

*   Superclasses: \[UNDER CONSTRUCTION: There could be more generic entities which connect to other events in an artefact's history.\]
*   Subclasses:
    *   [ProvAcquisition](#ProvAcquisition)
    *   \[UNDER CONSTRUCTION\]: Add other specific provenance types.
*   Definition: A generic _provenance_ entry, i.e. any event or part of an artefact's history during or after its theft, and relating to how the artefact ended up in its current location.
*   Usage notes: This class and all of its subclasses carry the name _provenance_, a term in used in Western historical and museological context to describe how (and why) an object got to its present location. It is supposed to be a neutral term for research purposes but masks or hides violences and injustices. We adopt the term here to describe what other institutions describe but don't identify with it.

ProvAcquisition

*   Superclasses:
    *   [ProvGeneric](#ProvGeneric)
*   Subclasses:
*   Definition:
*   Usage notes: Much like its super class term _provenance_, the term _acquisition_ is supposed to neutrally and generically describe how e.g. a state or museum came into possession of an object and masks that often these events were thefts, looting and other injust, violent actions. Like in the of the super class, we record the term because they use it./li>

### Datatype Entities

DateDescription

*   Definition:
*   Usage notes:
*   Required properties:
    *   [assigned\_text](#assigned_text)

LocationDescription

*   Definition:
*   Usage notes:
*   Required properties:
    *   [assigned\_text](#assigned_text)

* * *

Predicates
----------

### Top-level Predicates

Predicates of this kind are intended to be applied directly to members of the MoSA at the top level, this is however not a strict restriction.

name

*   Definition:
*   Usage notes:

digitally\_represented\_by

*   Domain:
*   Range: [DigitalRecord](#DigitalRecord)
*   Definition:
*   Usage notes:

physical\_object

*   Domain:
*   Range:
*   Definition:
*   Usage notes:

### Predicates pertaining to DigitalRecord

These predicates may also be used in other contexts, re-use is in fact encouraged (e.g. [assigned\_text](#assigned_text) can be used for attaching any text to any entity). The reason for calling most predicates "assigned\_" is to highlight the contestable nature of attributions.

identified\_by

*   Domain:[DigitalRecord](#DigitalRecord)
*   Range: a unique, persistent identifier (e.g. a URI)
*   Definition:
*   Usage notes:

assigned\_title

*   Domain:
*   Range:
*   Definition:
*   Usage notes:

assigned\_text

*   Domain:
*   Range:
*   Definition:
*   Usage notes:

assigned\_culture

*   Domain: any
*   Range: string (for now) in various languages
*   Definition:
*   Usage notes: Museum institutions typically assign cultures to objects (sometimes also known as "ethnic group" or "population"), this predicate can be used to record that. For now, we treat the assigned culture as a simple strig, eventually it should be a link (e.g. into a thesaurus).

assigned\_prov

*   Domain:
*   Range:
*   Definition:
*   Usage notes:

assigned\_date

*   Domain:
*   Range:
*   Definition:
*   Usage notes:

### Predicates pertaining to PhysicalManifestation

currently\_at

*   Domain:
*   Range:
    *   [Museum](#Museum)
    *   [LocationDescription](#LocationDescription)
*   Definition:
*   Usage notes: This property refers not (necessarily) to a precise geographical location (see [precise\_location](#precise_location) for that) but rather to a concept or (geo-polotical) entity with a geographical manifestitation, such as a country or a museum. This property may contain a [precise\_location](#precise_location) to further specify _where exacctly_ in the entity the object is, e.g. a room.

should\_be\_at

*   Domain:
*   Range:
*   Definition:
*   Usage notes:

assigned\_mnemonic

*   Domain:
*   Range: string
*   Definition: Mnemonic (or inventory number, object number, etc) given to the physical object where it either currently is ([currently\_at](#currently_at)) or, if applicable, should be ([should\_be\_at](#should_be_at)) and given to the object as a unique identifier.
*   Usage notes: Museums and other object-holding instituion use all sorts of standards for coining mnemonics, which is why the range of this property is basic strings. These mnemonics are (especially outside of digital context) a key way by which objects are identified in the places they are held, so this property should also be given for physical objects.

precise\_location

*   Domain:
*   Range:
    *   [LocationDescription](#LocationDescription)
    *   [geonames URI](https://www.geonames.org/)
*   Definition:
*   Usage notes:

depicted\_by

*   Domain:
*   Range:
*   Definition:
*   Usage notes: