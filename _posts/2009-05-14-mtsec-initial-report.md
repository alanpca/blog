---
layout: post
status: publish
published: false
title: MTSec Initial Report
author_login: admin
author_email: github@laudicina.net
excerpt: "I was asked by <a href=\"http:&#47;&#47;mavrinac.com&#47;\">Aaron Mavrinac<&#47;a>
  to write a report about what exactly MTSec currently does in the code - summary
  of what the standard hooks are doing, list of orders, list of objects, etc.&nbsp;
  For this report I focused mainly on the code itself, sort of the MTSec API as it
  stands now.&nbsp; This means that I have read all of the MTSec code already and
  have a good idea of what is happening within it.&nbsp; I plan to create a wiki page
  within the Thousand Parsec Wiki for others to be able to update my work as they
  see fit.&nbsp; Feel free to read my report on the MTSec game module source.\r\n"
wordpress_id: 64
wordpress_url: http://alanp.ca/blog/?p=64
date: '2009-05-14 21:11:50 -0400'
date_gmt: '2009-05-15 01:11:50 -0400'
categories:
- GSoC
tags:
- GSoC
- thousand parsec
comments: []
---
<p>I was asked by <a href="http:&#47;&#47;mavrinac.com&#47;">Aaron Mavrinac<&#47;a> to write a report about what exactly MTSec currently does in the code - summary of what the standard hooks are doing, list of orders, list of objects, etc.&nbsp; For this report I focused mainly on the code itself, sort of the MTSec API as it stands now.&nbsp; This means that I have read all of the MTSec code already and have a good idea of what is happening within it.&nbsp; I plan to create a wiki page within the Thousand Parsec Wiki for others to be able to update my work as they see fit.&nbsp; Feel free to read my report on the MTSec game module source.<br />
<a id="more"></a><a id="more-64"></a></p>
<hr &#47;>
<p style="margin-bottom: 0in;"><span style="font-size: medium;"><strong>Class MTSec<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>std::string MTSec::getName()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Returns the name of the Ruleset<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>std::string MTSec::getVersion()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Returns Version # (major.minor)<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::initGame()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Initializes the game:<&#47;p></p>
<ul>
<li>Creates an 	instance of Game.<&#47;li>
<li>Creates a 	turn from class MTSecTurn<&#47;li>
<li>Sets the 	game's turn process to MTSecTurn<&#47;li>
<li>Creates 	Galaxy &amp; Star System ObjectTypes and adds them to the game's 	Object Type Manager.<&#47;li>
<li>Sets the 	PlanetType &amp; FleetType to the integers returned from 	MTSecTurn::addNewObjectType()<&#47;li>
<li>Creates Order 	Types for: Nop, Move, Build, Colonise, SplitFleet &amp; MergeFleet<&#47;li>
<li>Sets the 	integer valued compMax to 13.<&#47;li><br />
<&#47;ul></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::create(.*)Prop()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Creates various properties.  Each property consists of a Category ID, Rank, Name, DisplayName, Description.  It also uses scheme in tcpl to do the calculations based on the property type.  I will definitely need to learn some basic scheme to further comprehend what is going on here.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Type of Props so far:<&#47;p></p>
<ul>
<li>Speed<&#47;li>
<li>AmmoCost<&#47;li>
<li>AmmoExplosiveness<&#47;li>
<li>AmmoSize<&#47;li>
<li>Firepower<&#47;li>
<li>MissileCost<&#47;li>
<li>MissileFirepower<&#47;li>
<li>MissileSize<&#47;li>
<li>HitPoints<&#47;li>
<li>HP<&#47;li>
<li>BuildTime<&#47;li>
<li>Armor<&#47;li>
<li>Colonise<&#47;li>
<li>NumAmmo<&#47;li>
<li>NumBayTypes<&#47;li>
<li>NumHulls<&#47;li><br />
<&#47;ul></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::create.*Comp()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Similar to the create.*Prop methods, but these create a Map (std::map<uint32_t, std::string>) of associated properties for each Component.  Components included are:<&#47;p></p>
<ul>
<li>ScoutHull<&#47;li>
<li>BattleScoutHull<&#47;li>
<li>CeriumAmmo<&#47;li>
<li>Cerium3Ammo<&#47;li>
<li>Cerium6Ammo<&#47;li>
<li>Cerium12Ammo<&#47;li>
<li>UraniumAmmo<&#47;li>
<li>AntiparticleAmmo<&#47;li>
<li>AntimatterAmmo<&#47;li>
<li>ThoriumAmmo<&#47;li>
<li>AlphaMissileBay<&#47;li>
<li>BetaMissileBay<&#47;li>
<li>GammaMissileBay<&#47;li>
<li>DeltaMissileBay<&#47;li><br />
<&#47;ul></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::createProperties()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Calls each create.*Prop()<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::createComponents()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Calls each create.*Comp()<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::createTechTree()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Calls createProperties() &amp; createComponents().<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>IGObject* MTSec::createAlphaCentauriSystem( IGObject* mw_galaxy)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Creates the Alpha Centauri Star System.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>IGObject* MTSec::createSiriusSystem( IGObject* mw_galaxy)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Creates the Sirius star system<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>static uint32_t myRandom( uint32_t  max)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Generates a random number between 1 and 'max'.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>IGObject* MTSec::createStarSystem( IGObject* mw_galaxy)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Creates a random start system<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>IGObject* MTSec::createSolSystem( IGObject *mw_galaxy)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Creates the Sol star system<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::createResources()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Creates the various resources:<&#47;p></p>
<ul>
<li>Ship Part<&#47;li>
<li>Home Planet<&#47;li>
<li>Uranium<&#47;li>
<li>Thorium<&#47;li>
<li>Cerium<&#47;li>
<li>Enriched 	Uranium<&#47;li>
<li>Massivium<&#47;li>
<li>Antiparticle<&#47;li>
<li>Antimatter<&#47;li><br />
<&#47;ul></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::createGame()<&#47;strong><&#47;p></p>
<ul>
<li>Creates a 	Universe<&#47;li>
<li>Adds 	contained objects (Galaxy)<&#47;li>
<li>Creates some 	Initial star systems (Sol, Alpha Centauri, Sirius, 45 randoms)<&#47;li><br />
<&#47;ul></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::startGame()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Checks if turn_length_over_threshold is empty, if so sets some default values:<&#47;p></p>
<ul>
<li>turn_length_over_threshold 	to 600<&#47;li>
<li>turn_player_threshold 	to 0<&#47;li>
<li>turn_length_under_threshold 	to 600<&#47;li><br />
<&#47;ul></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>bool MTSec::onAddPlayer(Player* player)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Just returns true?<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>Design* MTSec::createScoutDesign( Player* owner)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Creates a Scout Ship<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>Design* MTSec::createBattleScoutDesign( Player* owner)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Creates a Battle Scout Ship<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>IGObject* MTSec::createEmptyFleet( Player*     owner,<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>IGObject*   star,<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>std::string fleetName)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Creates an empty fleet, places it in orbit around the given IGObject *star.  Returns the fleet.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::makeNewPlayerFleet( Player* player, IGObject* star)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">From comments:<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; A new player's initial fleet always consists of two battle scouts.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47;<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; The designs for the scouts are one-offs, as far as the player<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; is concerned.  S&#47;he is unable to produce any more ships like<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; them, although they could create another design that functions<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; similarly.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Seems to create a new fleet by calling createEmptyFleet(), with 2 battle scout ships.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>IGObject* MTSec::makePlayerHomePlanet( Player* player, IGObject* star)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Creates the player's home planet, orbiting around the given *star.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>IGObject* MTSec::makeNewPlayerStarSystem( Player* player)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; Create a 'home star system' for a new player<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; These 'home systems' always consist of exactly one planet.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::setNewPlayerTech( Player* player)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; This routine sets a new player's initial tech level.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; New players can make any hull, see all stars.  This<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; doesn't leave anything for them to research.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSec::onPlayerAdded(Player* player)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; New players start with their own star systems, and an<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">&#47;&#47; initial fleet consisting of two scout ships.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in; font-weight: normal;"><strong><span style="font-size: medium;">Class MTSecTurn<&#47;span><&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSecTurn::doTurn()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Goes through the various processes that happen throughout a turn:<&#47;p></p>
<ol>
<li>
<p style="margin-bottom: 0in; font-weight: normal;">Iterates 	through all ObjectManager Ids<&#47;p></p>
<ol>
<li>
<p style="margin-bottom: 0in; font-weight: normal;">If the type 		of object is playettype or fleettype, it adds this object as a 		possible combatant.<&#47;p></p>
<ol>
<li>
<p style="margin-bottom: 0in; font-weight: normal;">Creates 			orders if necessary.<&#47;p><br />
<&#47;li><br />
<&#47;ol><br />
<&#47;li><br />
<&#47;ol><br />
<&#47;li></p>
<li>
<p style="margin-bottom: 0in; font-weight: normal;">Executes the 	Move<&#47;p><br />
<&#47;li></p>
<li>
<p style="margin-bottom: 0in; font-weight: normal;">Does the 	necessary Combat for the move<&#47;p><br />
<&#47;li></p>
<li>
<p style="margin-bottom: 0in; font-weight: normal;">Does other 	Orders (nop, buildfleet, colonise)<&#47;p><br />
<&#47;li></p>
<li>
<p style="margin-bottom: 0in; font-weight: normal;">Does the 	once-a-turn moves for each object.<&#47;p><br />
<&#47;li></p>
<li>
<p style="margin-bottom: 0in; font-weight: normal;">Finds the 	objects that are visible for each player<&#47;p><br />
<&#47;li><br />
<&#47;ol></p>
<p style="margin-bottom: 0in;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSecTurn::setPlanetType(uint32_t pt)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Sets the planettype to pt<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void MTSecTurn::setFleetType(uint32_t ft)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Sets the fleettype to ft<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>std::set<uint32_t> MTSecTurn::getContainerIds() const<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Returns the set of container Ids.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in;"><span style="font-size: medium;"><strong>Class Build<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>Build::Build() : Order()<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Constructor, Adds an order for fleetlist and fleetname.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void Build::createFrame(Frame *f, int pos)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets the current resource, sets turns.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Calls Order::createFrame().<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>std::map<uint32_t, std::pair<std::string, uint32_t> > Build::generateListOptions()<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Creates a map of options based on designs that are CategoryId 1.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>Result Build::inputFrame(Frame *f, uint32_t playerid)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Iterates through fleettypes, if fleettype is a usable design and the number to build exceeds 0 then we add number to UnderConstruction.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>bool Build::doOrder(IGObject *ob)<&#47;strong><&#47;span><&#47;p></p>
<ul>
<li><span style="font-size: small;">Creates 	a fleet<&#47;span><&#47;li>
<li><span style="font-size: small;">Adds 	the fleet to the container<&#47;span><&#47;li>
<li><span style="font-size: small;">Sets 	the ship type<&#47;span><&#47;li>
<li><span style="font-size: small;">Adds 	fleet to the universe<&#47;span><&#47;li><br />
<&#47;ul></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>Order* Build::clone() const<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Returns a clone of the Order based on type.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in;"><span style="font-size: medium;"><strong>Class Colonise<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>bool Colonise::doOrder(IGObject * ob)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">If the planet is not already colonised, it is close enough and there is a frigate available, the planet is colonised.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in;"><span style="font-size: medium;"><strong>Class Fleet<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>ObjectBehaviour* FleetType::createObjectBehaviour() const<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Returns an object of Fleet<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>Fleet::Fleet():OwnedObject()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Currently does nothing.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void Fleet::setDefaultOrderTypes()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Sets the default order types (No Operation, Move, Split Fleet &amp; Merge Fleet)<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void Fleet::addShips(uint32_t type, uint32_t number)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Adds number ships to fleet of type.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>bool Fleet::removeShips(uint32_t type, uint32_t number)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Removes number ships from fleet of type<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>uint32_t Fleet::numShips(uint32_t type)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Returns the number of ships in fleet &ldquo;type&rdquo;.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>std::map<uint32_t, uint32_t> Fleet::getShips() const{<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Returns a map of Ships in the Fleet<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>uint32_t Fleet::totalShips() const<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Returns the number of ships in the Fleet<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>uint32_t Fleet::getDamage() const<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Returns the damage of the Fleet<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void Fleet::setDamage(uint32_t nd)<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Sets the damage of the Fleet<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void Fleet::doOnceATurn()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Iterates through Planets owned by the Player, If damage isn't 0 it becomes 0.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">If the orders contain an instruction to Move, we set the vector.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>int Fleet::getContainerType()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Simply returns 0?<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><strong>void Fleet::setupObject()<&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Calls   OwnedObject::setupObject();<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Executes setSize(2).<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;">Some work may need to be done here.<&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in;"><span style="font-size: medium;"><strong>Class MergeFleet<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>bool MergeFleet::doOrder(IGObject * ob)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Merges two fleets together.  Removes the merged fleet from the universe.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>Order* MergeFleet::clone() const<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Clone operation for MergeFleet class, returns a MergeFleet with type set to the current type.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in; font-weight: normal;"><strong><span style="font-size: medium;">Class Move<&#47;span><&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void Move::setDest(const Vector3d &amp; ndest)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets the position to the ndest.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>int Move::getETA(IGObject *ob) const<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Returns the travel time to object ob<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void Move::createFrame(Frame * f, int pos)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets turns to the amount of time to get to position pos.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>bool Move::doOrder(IGObject * ob)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Processes a move order for the fleet pointed to by ob.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in; font-weight: normal;"><strong><span style="font-size: medium;">Class Nop &ndash; No Operation<&#47;span><&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void Nop::createFrame(Frame * f, int pos)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets turns to the timeparam's getTime() result.  Passes information to Order::createFrame()<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>Result Nop::inputFrame(Frame * f, uint32_t playerid)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets turns to the timeparam's getTime() result.  Returns the result that is given by passing f &amp; playerid to Order::inputFrame()<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>bool Nop::doOrder(IGObject * ob)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">If timeparam->getTime is greater than 1 then we decrement turns and timeparam's time.  If not, then we post a message of &ldquo;The object has finished it's delay and is now continuing&rdquo;.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in; font-weight: normal;"><strong><span style="font-size: medium;">Class Planet<&#47;span><&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>ObjectBehaviour* PlanetType::createObjectBehaviour() const<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Returns a new Planet instance.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void Planet::setDefaultOrderTypes()<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets the Default Order Types to &ldquo;Build Fleet&rdquo; and &ldquo;No Operation&rdquo;<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void Planet::doOnceATurn()<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Currently does nothing<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>int Planet::getContainerType()<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Returns &ldquo;2&rdquo;<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>std::map<uint32_t, std::pair<uint32_t, uint32_t> > Planet::getResources()<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Returns a map of the associated resources.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>uint32_t Planet::getResource(uint32_t restype) const<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Returns the TYPE of resource pointed to by restype.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void Planet::setResources(std::map<uint32_t, std::pair<uint32_t, uint32_t> > ress)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets resource of Planet to that of ress.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void Planet::addResource(uint32_t restype, uint32_t amount)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets up a map of the current resources, adds amount to the restype and sets the resource.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>bool Planet::removeResource(uint32_t restype, uint32_t amount)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets up a map of the current resources, removes amount from the restype and sets the resource.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in; font-weight: normal;"><strong><span style="font-size: medium;">Class SpaceObject<&#47;span><&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>Vector3d SpaceObject::getPosition() const<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Returns position of space object.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>Vector3d SpaceObject::getVelocity() const<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Returns velocity of space object.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>uint64_t SpaceObject::getSize() const<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Returns size of space object<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void SpaceObject::setPosition(const Vector3d &amp; np)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets position of space object.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void SpaceObject::setVelocity(const Vector3d &amp; nv)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets velocity of the space object.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void SpaceObject::setSize(uint64_t ns)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Sets the size of the space object.<&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in; font-weight: normal;"><strong><span style="font-size: medium;">Class SplitFleet<&#47;span><&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>std::map<uint32_t, std::pair<std::string, uint32_t> > SplitFleet::generateListOptions()<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><span style="font-weight: normal;">Gets a list of ships in the fleet, gets their options and returns a map of their options.<&#47;span><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>bool SplitFleet::doOrder(IGObject * ob)<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><span style="font-weight: normal;">Splits a fleet of ships into two fleets.<&#47;span><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in;"><&#47;p></p>
<hr &#47;>
<p style="margin-bottom: 0in; font-weight: normal;"><strong><span style="font-size: medium;">Class Universe<&#47;span><&#47;strong><&#47;p></p>
<p style="margin-bottom: 0in;"><&#47;p></p>
<p style="margin-bottom: 0in;"><span style="font-size: small;"><strong>void Universe::doOnceATurn()<&#47;strong><&#47;span><&#47;p></p>
<p style="margin-bottom: 0in; font-weight: normal;"><span style="font-size: small;">Executes the once-a-turn requirements for the Universe.  Currently, this implements a simple incrementation and time update.<&#47;span><&#47;p></p>
