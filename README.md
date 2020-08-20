# Air Purifier

This design was inspired by kels316's [DIY Air Purifier](https://github.com/Kels316/DIY-Air-Purifier/) and numerous other xiaomi derived air purifier designs available on thingiverse.

I didn't have easy access to the specific cylindrical HEPA filter and this design was originally intended to simply accept a different size. I went on to add UV sterilization to more closely feature-match an old commercial filtration unit which required replacement.

UV sterilization is provided by a 3W GTL3 UVC bulb which may also produce small amounts of ozone (depending on envelope coatings). This is ballasted by a capacitive dropper which provides the bulb ~10VAC at a couple hundred milliamps.

GTL3 bulbs have an interesting self-ignition design, they initially operate as a thermionic emitter using a filament with a negative thermal coefficient until a sufficient mercury plasma is generated in the envelope. The plasma cloud then conducts the majority of the current once the filament reaches a high-resistance state. AC operation is preferred over DC to prevent premature erosion of one end of the filament.

Airflow is provided by an inexpensive computer case fan operating at 12V. Due to the simplicity of the circuit and inherent safety of a fully enclosed device another capacitive dropper is used, followed by a full bridge rectifier and zener for rough regulation.

Both capacitive droppers have bleeder resistors in parallel with the class X capacitors to prevent shocks off the end of the cable. The 120VAC input is protected with a fuse, MOV and inrush current limiter. I chose to install an in-line switch into the power cable but this is optional.

In order to maximize the exposure of the air-stream to UVC radiation the area immediately surrounding the GTL3 bulb is sheathed in aluminum foil which will reflect the radiation through the chamber multiple times as well as protect the plastic from degradation. Other surfaces of the baffle are painted with white (titanium dioxide) interior house paint for protection. According to the scientific literature TiO is an efficient absorber of UVC radiation and should reduce the amount which escapes through the baffle via reflection. It also photocatalytically destroys VOCs but I'm not clear on if a paint coating has this ability or if it requires special preparation of the TiO particles.


## File Structure

```
cad    -- FreeCAD 0.19 design documents using Assembly4 workbench
          Top level assembly document 0_top_level_uvc_air_filter.FCStd
stl    -- Exported models for 3D printing

PCB    -- Power supply PCB design files and BOM
gerber -- Zipped gerber files for PCB fabhouse
sim    -- ltspice simulation of power supply
```


## Bill Of Materials

| Qty | Part                           | Link                                                                     |
|-----|--------------------------------|--------------------------------------------------------------------------|
| 1   | PSU PCB                        | Fab from gerbers/BOM                                                     |
| 1   | Air Filter                     | https://www.amazon.com/gp/product/B08245MH67/ or similar 88mm dia filter |
| 4   | Vibration dampening fan rivets | https://www.amazon.com/gp/product/B00H9905KA/ or similar                 |
| 1   | GTL3 Bulb                      | https://www.amazon.com/gp/product/B081RSZT6S/ or similar                 |
| 1   | E17 Socket                     | https://www.amazon.com/gp/product/B07J4ZTYWZ/ or similar                 |
| 23  | M3 Nut                         | https://www.mcmaster.com/90592A085/ or similar                           |
| 21  | M3x16 Bolt                     | https://www.mcmaster.com/91290A120/ or similar                           |
| 2   | M3x8 Bolt (For E17 socket)     | https://www.mcmaster.com/91290A113/ or similar                           |
| 2   | M3 Washer (For E17 socket)     | https://www.mcmaster.com/91166a210/ or similar                           |
| 1   | Power Cable                    | https://www.mcmaster.com/7248K21/ or similar                             |
| 1   | Inline Switch (Optional)       | https://www.mcmaster.com/14695K91/ or similar                            |
| 1   | 120mm Fan                      | Purchase or recycle from PC                                              |
| 1   | Aluminum Foil                  | Purchase                                                                 |
| 2   | Zipties (For Power Cable)      | Purchase                                                                 |
| 4   | M3x5 Standoff                  | 3D Print or purchase                                                     |
| 3   | Foot                           | 3D Print in TPU or purchase compatible feet                              |
| 1   | Upper Baffle                   | 3D Print                                                                 |
| 1   | Top Cap                        | 3D Print                                                                 |
| 1   | Lower Baffle                   | 3D Print                                                                 |
| 1   | Fan Cover                      | 3D Print                                                                 |
| 1   | Bottom Cap                     | 3D Print                                                                 |
| 1   | Baffle Cap Bracket             | 3D Print                                                                 |
| 1   | Baffle Cap                     | 3D Print                                                                 |


## Assembly Notes

The supplied gerber zip file is submittable to JLCPCB/OSHPARK or other PCB fabhouse. It is important that the AC series capacitors are at least class X1 to prevent blown fuses or fire. Take care when testing this circuit, the outputs float and may have a 120VAC potential to ground so don't touch it! It may also destroy non-isolated oscilloscopes or other ground-referenced test equipment. UVC light is dangerous to the eyes and causes skin cancer, damages plastic and will even kill houseplants with sufficient exposure. Don't stare at the bulb, only run open-air tests briefly and preferably view it through the screen of a digital camera or UV filtered glasses.

Total 3D printing time on my ender 3 with 20% infill was about 75 hours and used approximately 500g of filament.

Coat innermost surfaces of Bottom Cap with TiO paint, as well as outer surfaces of Upper and Lower Baffle and inner surfaces of Baffle Cap.

For ease of construction build the Internal Baffle Assembly first and glue aluminum foil to its inner surface. Then assemble into Top Cap.

Build Bottom Cap Assembly and Fan Cover Assembly as independent units. Ensure fan blows air outward through the vent holes. When screwing feet into Bottom Cap ensure the bolts do not sit excessively proud of the Bottom Cap surface where they would interfere with the filter's foam seal.

When building Baffle Cap Assembly start by installing the Baffle Cap Bracket, then the E17 Socket. The E17 mounting holes were oversized and required washers. Feed E17 wires through the holes in the Baffle Cap and Bracket before installing fasteners. Use short bolts to leave room on rear face for the PCB. The two captive nut features on the top face of the Baffle Cap were tight but the nuts seated as the bolts were screwed in. Afterward the PCB can be installed with the standoffs and the E17 wires can be connected. At that point the GTL3 bulb can be screwed into the socket and the assembly can be attached to the Top Cap.

For stability the Bottom Cap Assembly, Filter and Top Cap Assembly can be fit together before wiring the Power Cable. Plug the fan into the PCB and carefully slot the power cable into the mouse-hole on the edge of the Fan Cover. With the Fan Cover seated over the Top Cap a ziptie can be applied to the cable up against the cover to prevent it from being pushed inside the unit. The Fan Cover can then be temporarily removed to install a second ziptie on the cable against the inner surface of the Fan Cover to prevent the cable from being pulled out of the PCB. The Fan Cover can then be screwed into the Top Cap taking care that the bolts do not sit excessively proud of the surface where they would interfere with the filter's foam seal.

