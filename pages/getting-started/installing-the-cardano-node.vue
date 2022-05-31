<template>
    <ContentWrap>
        <Content>
            <ContentTitle>Installing the Cardano node</ContentTitle>
            <div class="main">
                <h2 class="heading2" id="downloadingpre-compiledexecutables">Downloading pre-compiled executables</h2>
                <p class="paragraph">You can install the Cardano node and cli using
                    <a href="https://github.com/input-output-hk/cardano-node#linux-executable" target="_blank"
                        rel="noopener noreferrer">pre-compiled executable files</a>
                    for your platform.
                </p>
                <h2 class="heading2" id="buildingfromsource">Building from source</h2>
                <p class="paragraph">Alternatively, if you want to build from source, there are two options
                    available to you. Depending on your build tool preference, you can build from
                    the source code using either of the following:</p>
                <ul>
                    <li><a href="https://github.com/input-output-hk/cardano-node/blob/master/doc/getting-started/install.md/"
                            target="_blank" rel="noopener noreferrer">cabal: building the node</a></li>
                    <li><a href="https://github.com/input-output-hk/cardano-node/blob/master/doc/getting-started/building-the-node-using-nix.md/"
                            target="_blank" rel="noopener noreferrer">Nix: building the node</a></li>
                </ul>
                <p class="paragraph">Please refer to the <a
                        href="https://github.com/input-output-hk/cardano-node/releases/latest" target="_blank"
                        rel="noopener noreferrer">cardano-node releases page</a> to ensure you are working with the
                    latest version of the node.</p>
                <p class="paragraph">Once you have installed the node, you need to
                    <a href="https://github.com/input-output-hk/cardano-node/blob/master/doc/getting-started/understanding-config-files.md/"
                        target="_blank" rel="noopener noreferrer">specify the configuration parameters</a>.
                </p>
                <h2 class="heading2" id="usingdocker">Using Docker</h2>
                <p class="paragraph">There is also a Docker image available that you can use. </p>
                <h3 class="heading3" id="settingupdocker">Setting up Docker</h3>
                <ol>
                    <li>Download and install Docker/Docker Desktop from the <a
                            href="https://docs.docker.com/get-docker/" target="_blank" rel="noopener noreferrer">Docker
                            site</a>.</li>
                    <li>If using Windows or Mac, ensure you have allocated enough RAM to Docker (we recommend setting
                        the RAM to 8GB in the Docker Desktop requirements) and start the Docker daemon, as described in
                        the Docker instructions. Note that Docker on Linux, there are no RAM limits for containers by
                        default.</li>
                </ol>
                <h3 class="heading3" id="settingupthecardanonode">Setting up the Cardano node</h3>
                <ol>
                    <li>Download the correct <code>cardano-node</code> image:</li>
                </ol>
                <p class="paragraph"><code>docker image pull inputoutput/cardano-node:&lt;TAG&gt;</code></p>
                <p class="paragraph">where <code>&lt;TAG&gt;</code> is the tag for the version that you require (e.g.
                    <code>latest</code> for the most recent stable version, or <code>1.27.0</code> for node version
                    1.27.0).</p>
                <ol start="2">
                    <li>Create local <code>cardano-node-data</code> and <code>cardano-node-ipc</code> volumes:</li>
                </ol>
                <pre
                    class="css-fkgcw9 ev1gfv90"><pre><pre class="prism-code language-javascript pre" style="color:#9CDCFE;background-color:#1E1E1E" p="3"><div class="token-line"><span class="token plain">docker volume create cardano</span><span class="token operator" style="color:rgb(212, 212, 212)">-</span><span class="token plain">node</span><span class="token operator" style="color:rgb(212, 212, 212)">-</span><span class="token plain">data</span></div><div class="token-line"><span class="token plain">docker volume create cardano</span><span class="token operator" style="color:rgb(212, 212, 212)">-</span><span class="token plain">node</span><span class="token operator" style="color:rgb(212, 212, 212)">-</span><span class="token plain">ipc</span></div></pre>
                </pre>
                </pre>
                <h3 class="heading3" id="runningthecardanonode">Running the Cardano node</h3>
                <ol>
                    <li>Run a passive node that is connected to the correct network. For example, for a
                        <code>mainnet</code> node:</li>
                </ol>
                <p class="paragraph">
                    <code>docker run -e NETWORK=mainnet -v cardano-node-ipc:/ipc -v cardano-node-data:/data inputoutput/cardano-node</code>
                </p>
                <p class="paragraph">This creates a persistent docker environment for the node, where <code>/ipc</code>
                    in the Docker container is connected to the logical <code>cardano-node-ipc</code> volume, and
                    <code>/data</code> is connected to the <code>cardano-node-data</code> volume. Note that you should
                    change <code>NETWORK=mainnet</code> if you are connecting to a different network (eg a testnet).
                </p>
                <h3 class="heading3" id="passingexplicitconfigurationparameters">Passing Explicit Configuration
                    Parameters</h3>
                <p class="paragraph">You may also run the node with specific parameters:</p>
                <p class="paragraph">
                    <code>docker run -v cardano-node-ipc:/ipc -v cardano-node-data:/data inputoutput/cardano-node run --help</code>
                </p>
                <p class="paragraph">If there is no pre-defined network configuration, you will need to download the
                    specified configuration files, copy these to the persistent Docker volume, and pass the parameters
                    on the command line:</p>
                <p class="paragraph">
                    <code>docker run -v cardano-node-ipc:/ipc -v cardano-node-data:/data inputoutput/cardano-node run --config ... --topology ... --...</code>
                </p>
                <h3 class="heading3" id="runningcardanoclicommands">Running Cardano CLI commands</h3>
                <p class="paragraph">You can now run normal Cardano CLI commands, for example,</p>
                <pre
                    class="css-fkgcw9 ev1gfv90"><pre><pre class="prism-code language-javascript pre" style="color:#9CDCFE;background-color:#1E1E1E" p="3"><div class="token-line"><span class="token keyword module" style="color:rgb(86, 156, 214)">export</span><span class="token plain"> </span><span class="token constant" style="color:rgb(100, 102, 149)">CLI</span><span class="token operator" style="color:rgb(212, 212, 212)">=</span><span class="token string" style="color:rgb(206, 145, 120)">'docker run -it --entrypoint cardano-cli -e NETWORK=mainnet -e CARDANO_NODE_SOCKET_PATH=/ipc/node.socket -v cardano-node-ipc:/ipc inputoutput/cardano-node'</span><span class="token plain"></span></div><div class="token-line"><span class="token plain">$</span><span class="token constant" style="color:rgb(100, 102, 149)">CLI</span><span class="token plain"> version</span></div><div class="token-line"><span class="token plain">$</span><span class="token constant" style="color:rgb(100, 102, 149)">CLI</span><span class="token plain"> query tip </span><span class="token operator" style="color:rgb(212, 212, 212)">--</span><span class="token plain">mainnet</span></div><div class="token-line"><span class="token plain">$</span><span class="token constant" style="color:rgb(100, 102, 149)">CLI</span><span class="token plain"> transaction build</span><span class="token operator" style="color:rgb(212, 212, 212)">-</span><span class="token plain">raw </span><span class="token spread operator" style="color:rgb(212, 212, 212)">...</span><span class="token plain"> </span><span class="token operator" style="color:rgb(212, 212, 212)">--</span><span class="token plain">mainnet</span></div></pre>
                </pre>
                </pre>
                <p class="paragraph">You need to specify <code>CARDANO_NODE_SOCKET_PATH</code> to point to the correct
                    location in the container (<code>/ipc/node.socket</code> is the standard location).</p>
                <h3 class="heading3" id="runningashellinthedockercontainer">Running a Shell in the Docker Container</h3>
                <p class="paragraph">To run a shell in the container (so that you can inspect or change settings, for
                    example), use the <code>bash</code> or <code>sh</code> entry point.</p>
                <p class="paragraph">
                    <code>docker run -it --entrypoint bash -v cardano-node-ipc:/ipc -v cardano-node-data:/data inputoutput/cardano-node</code>
                </p>
                <p class="paragraph">You may now run any commands that you require with full access to the container's
                    file systems.</p>
                <pre
                    class="css-fkgcw9 ev1gfv90"><pre><pre class="prism-code language-javascript pre" style="color:#9CDCFE;background-color:#1E1E1E" p="3"><div class="token-line"><span class="token plain">bash</span><span class="token operator" style="color:rgb(212, 212, 212)">-</span><span class="token number" style="color:rgb(181, 206, 168)">4.4</span><span class="token plain"># cd </span><span class="token operator" style="color:rgb(212, 212, 212)">/</span><span class="token plain">data</span><span class="token operator" style="color:rgb(212, 212, 212)">/</span><span class="token plain">db</span></div><div class="token-line"><span class="token plain">bash</span><span class="token operator" style="color:rgb(212, 212, 212)">-</span><span class="token number" style="color:rgb(181, 206, 168)">4.4</span><span class="token plain"># ls</span></div><div class="token-line"><span class="token plain">immutable  ledger  lock  protocolMagicId  volatile</span></div><div class="token-line"><span class="token plain">bash</span><span class="token operator" style="color:rgb(212, 212, 212)">-</span><span class="token number" style="color:rgb(181, 206, 168)">4.4</span><span class="token plain"># </span></div></pre>
                </pre>
                </pre>
                <p class="paragraph">Alternatively, you can start the node container with a name.</p>
                <p class="paragraph">
                    <code>docker run --name cardano-node -e NETWORK=mainnet -v cardano-node-ipc:/ipc -v cardano-node-data:/data inputoutput/cardano-node</code>
                </p>
                <p class="paragraph">In a separate terminal instance, run shell in an existing container.</p>
                <p class="paragraph"><code>docker exec -it cardano-node bash</code></p>
                <h3 class="heading3" id="copyingfilesto/fromthedockercontainer">Copying files to/from the Docker
                    Container</h3>
                <p class="paragraph">To copy files to/from the docker container use <code>docker cp</code>.</p>
                <p class="paragraph">For example, if the process ID of the running container is
                    <code>760199bf3561</code></p>
                <pre
                    class="css-fkgcw9 ev1gfv90"><pre><pre class="prism-code language-javascript pre" style="color:#9CDCFE;background-color:#1E1E1E" p="3"><div class="token-line"><span class="token plain">kh@vulcan</span><span class="token operator" style="color:rgb(212, 212, 212)">:</span><span class="token operator" style="color:rgb(212, 212, 212)">~</span><span class="token plain">$ docker ps</span></div><div class="token-line"><span class="token plain"></span><span class="token constant" style="color:rgb(100, 102, 149)">CONTAINER</span><span class="token plain"> </span><span class="token constant" style="color:rgb(100, 102, 149)">ID</span><span class="token plain">   </span><span class="token constant" style="color:rgb(100, 102, 149)">IMAGE</span><span class="token plain">                      </span><span class="token constant" style="color:rgb(100, 102, 149)">COMMAND</span><span class="token plain">                  </span><span class="token constant" style="color:rgb(100, 102, 149)">CREATED</span><span class="token plain">       </span><span class="token constant" style="color:rgb(100, 102, 149)">STATUS</span><span class="token plain">       </span><span class="token constant" style="color:rgb(100, 102, 149)">PORTS</span><span class="token plain">     </span><span class="token constant" style="color:rgb(100, 102, 149)">NAMES</span><span class="token plain"></span></div><div class="token-line"><span class="token plain"></span><span class="token number" style="color:rgb(181, 206, 168)">760199</span><span class="token plain">bf3561   inputoutput</span><span class="token operator" style="color:rgb(212, 212, 212)">/</span><span class="token plain">cardano</span><span class="token operator" style="color:rgb(212, 212, 212)">-</span><span class="token plain">node   </span><span class="token string" style="color:rgb(206, 145, 120)">"/nix/store/p435ajna…"</span><span class="token plain">   </span><span class="token spread operator" style="color:rgb(212, 212, 212)">...</span><span class="token plain"></span></div></pre>
                </pre>
                </pre>
                <p class="paragraph">Then to copy the <code>immutable</code> directory (if you have a cached version),
                    for example, you can:</p>
                <p class="paragraph"><code>docker cp db/immutable 760199bf3561:/data/db/immutable</code></p>
                <p class="paragraph">You can also mount local directories for use by the container. For example to share
                    the <code>db</code> and <code>node-ipc</code> directories, you could:</p>
                <p class="paragraph">
                    <code>docker run ---mount type=bind,source="$(pwd)/db/",target=/data/db  --mount type=bind,source="$(pwd)/node-ipc",target=/ipc inputoutput/cardano-node ...</code>
                </p>
                <h4 class="heading4" id="relatedtopics">Related Topics</h4>
                <ul>
                    <li><a href="/getting-started/use-cli" target="_self" rel="noopener noreferrer">Using the command
                            line interface</a></li>
                </ul>
            </div>
            <ContentPosts next-title="Using the command line interface" next-link="/getting-started/use-cli" />
        </Content>
        <ContentAnchor>
            <li><a
                    href="#downloadingpre-compiledexecutables">Downloading
                    pre-compiled executables</a></li>
            <li><a
                    href="#buildingfromsource">Building from source</a>
            </li>
            <li><a
                    href="#usingdocker">Using Docker</a></li>
        </ContentAnchor>
    </ContentWrap>
</template>