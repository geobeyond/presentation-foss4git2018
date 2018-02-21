## WPS chained call

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Execute version="1.0.0" service="WPS" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.opengis.net/wps/1.0.0" xmlns:wfs="http://www.opengis.net/wfs" xmlns:wps="http://www.opengis.net/wps/1.0.0" xmlns:ows="http://www.opengis.net/ows/1.1" xmlns:gml="http://www.opengis.net/gml" xmlns:ogc="http://www.opengis.net/ogc" xmlns:wcs="http://www.opengis.net/wcs/1.1.1" xmlns:xlink="http://www.w3.org/1999/xlink" xsi:schemaLocation="http://www.opengis.net/wps/1.0.0 http://schemas.opengis.net/wps/1.0.0/wpsAll.xsd">
	<Identifier>
		geoavalanche:DangerIndex
	</Identifier>
	<DataInputs>
		<Input>
			<Identifier>
				FeatureCollection
			</Identifier>
			<Reference mimeType="text/xml" xlink:href="http://geoserver/wps" method="POST">
				<Body>
					<Execute version="1.0.0" service="WPS">
						<Identifier>
							geoavalanche:SnowPack
						</Identifier>
						<DataInputs>
							<Input>
								<Identifier>
									FeatureCollection
								</Identifier>
								<Reference mimeType="text/xml" xlink:href="http://geoserver/wps" method="POST">
									<Body>
										<Execute version="1.0.0" service="WPS">
											<Identifier>
												geoavalanche:Crowd
											</Identifier>
											<DataInputs>
												<Input>
													<Identifier>
														FeatureCollection
													</Identifier>
													<Reference mimeType="text/xml" xlink:href="http://geoserver/wps" method="POST">
														<Body>
															<Execute version="1.0.0" service="WPS">
																<Identifier>
																	geoavalanche:ATEINorm
																</Identifier>
																<DataInputs>
																	<Input>
																		<Identifier>
																			dem
																		</Identifier>
																		<Reference mimeType="image/tiff" xlink:href="http://geoserver/wcs" method="POST">
																			<Body>
																				<GetCoverage service="WCS" version="1.1.1">
																					<Identifier>
																						geoavalanche:eu_dem_v11_E40N20_3035
																					</Identifier>
																					<DomainSubset>
																						<BoundingBox crs="http://www.opengis.net/gml/srs/epsg.xml#3035">
																							<LowerCorner>
																								4000000.0 2000000.0
																							</LowerCorner>
																							<UpperCorner>
																								5000000.0 3000000.0
																							</UpperCorner>
																						</BoundingBox>
																					</DomainSubset>
																					<Output format="image/tiff" />
																				</GetCoverage>
																			</Body>
																		</Reference>
																	</Input>
																</DataInputs>
															</Execute>
														</Body>
													</Reference>
												</Input>
											</DataInputs>
										</Execute>
									</Body>
								</Reference>
							</Input>
						</DataInputs>
					</Execute>
				</Body>
			</Reference>
		</Input>
```